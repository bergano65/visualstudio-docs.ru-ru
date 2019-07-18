---
title: CA1063. Правильно реализуйте IDisposable | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 90f218165c0543c1881857191efd202717c6e372
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820880"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063. Правильно реализуйте IDisposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 `IDisposable` не реализован правильно. Ниже перечислены некоторые причины возникновения этой проблемы:

- IDisposable — это повторно реализован в классе.

- Завершение подготовки повторно переопределяется.

- Переопределяется метод Dispose.

- Dispose() не является открытым, запечатанным или с именем Dispose.

- Dispose(bool) не защищенный виртуальный и незапечатанный.

- В незапечатанных типов Dispose() необходимо вызвать Dispose(true).

- Для незапечатанных типов реализации Finalize не вызывает один или оба Dispose(bool) или метод завершения класса.

  Нарушение любого из этих шаблонов приведет к выводу предупреждения.

  Каждый незапечатанного корневого типа IDisposable необходимо предоставить собственный защищенный виртуальный void Dispose(bool) метод. Dispose() должны вызывать Dispose(true) и Finalize должен вызывать Dispose(false). Если вы создаете незапечатанного корневого типа IDisposable, необходимо определить Dispose(bool) и вызывать его. Дополнительные сведения см. в разделе [очистки неуправляемых ресурсов](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) в [рекомендации по разработке Framework](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) раздел документации .NET Framework.

## <a name="rule-description"></a>Описание правила
 Все типы IDisposable должны правильно реализовывать шаблон "Dispose".

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Проверьте код и определите, какой из указанных ниже способов устранения нарушения.

- Удалите IDisposable из списка интерфейсов, реализуемые {0} и вместо него переопределите реализацию базового класса Dispose.

- Удалите метод завершения из типа {0}, переопределите Dispose (bool disposing) и поместите логику завершения в ветвь кода, где значение «disposing» равно false.

- Удалить {0}, переопределите Dispose (bool disposing) и поместите логику освобождения в ветвь кода, где «disposing» равно true.

- Убедитесь, что {0} объявляется как открытый и запечатанный.

- Переименовать {0} на «Dispose» и убедитесь, что он объявлен как открытый и запечатанный.

- Убедитесь, что {0} объявлен как защищенный, виртуальный и незапечатанный.

- Изменить {0} так, чтобы он вызывал Dispose(true), затем вызывает сборщик Мусора. SuppressFinalize для текущего экземпляра объекта («this» или «Me» в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), а затем возвращает.

- Изменить {0} , чтобы он вызывал Dispose(false) и затем возвращает.

- Если вы создаете класс незапечатанного корневого IDisposable, убедитесь, что реализации IDisposable по шаблону, описанное ранее в этом разделе.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдокода
 Следующий псевдокод представлен общий пример реализации Dispose(bool) в класс, использующий управляемые и машинные ресурсы.

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
