---
title: 'CA1063: правильно реализуйте IDisposable | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04691d2344b232906676180122ad67fff5405891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539364"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063. Правильно реализуйте IDisposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 `IDisposable` реализован неправильно. Ниже перечислены некоторые причины этой проблемы.

- Интерфейс IDisposable повторно реализован в классе.

- Finalize переопределяется повторно.

- Dispose переопределяется.

- Dispose () не является общедоступным, запечатанным или именованным удалением.

- Dispose (bool) не является защищенным, виртуальным или незапечатанным.

- В незапечатанных типах метод Dispose () должен вызывать Dispose (true).

- Для незапечатанных типов реализация Finalize не вызывает ни метод Dispose (bool), ни метода завершения класса case.

  Нарушение какого либо из этих шаблонов вызовет это предупреждение.

  Каждый незапечатанный корневой тип IDisposable должен предоставлять собственный защищенный виртуальный метод Dispose (bool). Метод Dispose () должен вызывать Dispose (true) и Finalize должен вызывать Dispose (false). При создании незапечатанного корневого типа IDisposable необходимо определить метод Dispose (bool) и вызвать его. Дополнительные сведения см. в разделе [Очистка неуправляемых ресурсов](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) раздела рекомендации по [проектированию платформы](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) .NET Framework документации.

## <a name="rule-description"></a>Описание правила
 Все типы IDisposable должны правильно реализовывать шаблон "Dispose".

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Проверьте код и определите, какое из следующих разрешений исправит это нарушение.

- Удалите IDisposable из списка интерфейсов, реализованных с помощью, {0} а вместо этого Переопределите реализацию Dispose базового класса.

- Удалите метод завершения из типа {0} , переопределите Dispose (bool disposing) и поставьте логику финализации в путь кода, где "disposing" имеет значение false.

- Удалите {0} , переопределите Dispose (bool disposing) и поставьте логику Dispose в путь кода, где "disposing" имеет значение true.

- Убедитесь, что {0} объявлен как открытый и запечатанный.

- Переименуйте {0} в \ "Dispose \" и убедитесь, что он объявлен как открытый и запечатанный.

- Убедитесь, что {0} объявлено как защищенное, виртуальное и незапечатанное.

- Измените {0} таким образом, чтобы он вызывал метод Dispose (true), а затем ВЫЗЫВАЛ GC. SuppressFinalize в текущем экземпляре объекта ("this" или "Me" in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), а затем возвращает.

- Измените {0} таким образом, чтобы он вызывал Dispose (false), а затем возвращал.

- При написании незапечатанного корневого класса IDisposable убедитесь, что реализация IDisposable соответствует шаблону, описанному ранее в этом разделе.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдокода
 В следующем псевдокоде приведен общий пример реализации метода Dispose (bool) в классе, использующем управляемые и машинные ресурсы.

```
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

// Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }
    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```
