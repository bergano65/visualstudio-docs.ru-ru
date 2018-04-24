---
title: 'CA1063: следует правильно реализовывать IDisposable'
ms.date: 02/12/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9205c20730681969550c3a2368e6ec889056648b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: следует правильно реализовывать IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

`IDisposable` реализован неверно. Ниже перечислены некоторые причины возникновения этой проблемы:

- Интерфейс IDisposable пересоздания в классе.

- Завершение переопределяется повторно.

- Метод Dispose переопределяется.

- Метод Dispose() не является открытым, запечатанным или с именем Dispose.

- Dispose(bool) не является защищенным, виртуальным или незапечатанном.

- В незапечатанных типов Dispose() необходимо вызвать Dispose(true).

- Для незапечатанных типов реализации Finalize не вызывает один или оба Dispose(bool) или метод завершения класса.

Нарушение любого из этих шаблонов приведет к выводу предупреждения.

Каждый незапечатанный тип, который объявляет и реализует интерфейс IDisposable необходимо предоставить свой собственный защищенный виртуальный void Dispose(bool) метод. Метод Dispose() следует вызывать Dipose(true) и Finalize должен вызывать Dispose(false). Если вы создаете незапечатанный тип, который объявляет и реализует интерфейс IDisposable, необходимо определить Dispose(bool) и вызывать его. Дополнительные сведения см. в разделе [Очистка неуправляемых ресурсов](/dotnet/standard/garbage-collection/unmanaged) в [рекомендации по разработке .NET Framework](/dotnet/standard/design-guidelines/index).

## <a name="rule-description"></a>Описание правила

Все типы IDisposable должны правильно реализовывать шаблон "Dispose".

## <a name="how-to-fix-violations"></a>Устранение нарушений

Проверьте код и определите, какой из указанных ниже способов для устранения нарушения.

- Удалите IDisposable из списка интерфейсов, которые реализуются {0} и вместо него переопределите реализацию базового класса Dispose.

- Удалите метод завершения из типа {0}, переопределите Dispose (bool disposing) и поместите логику завершения в ветвь кода, где «disposing» равно false.

- Удалить {0}, переопределите Dispose (bool disposing) и поместите логику освобождения в ветвь кода, где «disposing» равно true.

- Убедитесь, что этот {0} объявлен как открытый и запечатанный.

- Переименуйте {0} на «Dispose» и убедитесь, что он объявлен как открытый и запечатанный.

- Убедитесь в том, что этот {0} объявлен как защищенный, виртуальный и незапечатанный.

- Измените {0}, чтобы он вызывал Dispose(true), затем вызывает GC. SuppressFinalize для текущего экземпляра объекта («this» или «Me» в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), а затем возвращает.

- Измените {0}, чтобы он вызывал Dispose(false) и затем возвращает.

- Если создается незапечатанный тип, который объявляет и реализует интерфейс IDisposable, убедитесь, что реализация IDisposable строятся по схеме, описанной ранее в этом разделе.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдокода

Следующий псевдокод представлен общий пример реализации Dispose(bool) в классе, который использует управляемые и машинные ресурсы.

```csharp
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