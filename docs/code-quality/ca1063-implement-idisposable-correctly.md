---
title: "Ca1063 следует: Реализовывать IDisposable правильно | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 33c9b3d7b3cdcfc49c3fac14e5ba3a2dcfc2fc49
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: следует правильно реализовывать IDisposable
|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 `IDisposable`реализован неверно. Ниже перечислены некоторые причины возникновения этой проблемы:  
  
-   Интерфейс IDisposable пересоздания в классе.  
  
-   Завершение переопределяется повторно.  
  
-   Метод Dispose переопределяется.  
  
-   Метод Dispose() не является открытым, запечатанным или с именем Dispose.  
  
-   Dispose(bool) не является защищенным, виртуальным или незапечатанном.  
  
-   В незапечатанных типов Dispose() необходимо вызвать Dispose(true).  
  
-   Для незапечатанных типов реализации Finalize не вызывает один или оба Dispose(bool) или метод завершения класса.  
  
 Нарушение любого из этих шаблонов приведет к выводу предупреждения.  
  
 Каждый незапечатанного корневого типа IDisposable необходимо предоставить свой собственный защищенный виртуальный void Dispose(bool) метод. Метод Dispose() следует вызывать Dipose(true) и Finalize должен вызывать Dispose(false). При создании незапечатанного корневого типа IDisposable необходимо определить Dispose(bool) и вызывать его. Дополнительные сведения см. в разделе [очистки неуправляемых ресурсов](/dotnet/standard/garbage-collection/unmanaged) в [Framework рекомендации по проектированию](/dotnet/standard/design-guidelines/index) раздел документации платформы .NET Framework.  
  
## <a name="rule-description"></a>Описание правила  
 Все типы IDisposable должны правильно реализовывать шаблон "Dispose".  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Проверьте код и определите, какой из указанных ниже способов для устранения нарушения.  
  
-   Удалите IDisposable из списка интерфейсов, которые реализуются {0} и вместо него переопределите реализацию базового класса Dispose.  
  
-   Удалите метод завершения из типа {0}, переопределите Dispose (bool disposing) и поместите логику завершения в ветвь кода, где «disposing» равно false.  
  
-   Удалить {0}, переопределите Dispose (bool disposing) и поместите логику освобождения в ветвь кода, где «disposing» равно true.  
  
-   Убедитесь, что этот {0} объявлен как открытый и запечатанный.  
  
-   Переименуйте {0} на «Dispose» и убедитесь, что он объявлен как открытый и запечатанный.  
  
-   Убедитесь в том, что этот {0} объявлен как защищенный, виртуальный и незапечатанный.  
  
-   Измените {0}, чтобы он вызывал Dispose(true), затем вызывает GC. SuppressFinalize для текущего экземпляра объекта («this» или «Me» в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), а затем возвращает.  
  
-   Измените {0}, чтобы он вызывал Dispose(false) и затем возвращает.  
  
-   При написании незапечатанного корневого класса IDisposable, убедитесь в том, что реализация IDisposable строятся по схеме, описанной ранее в этом разделе.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="pseudo-code-example"></a>Пример псевдокода  
 Следующий псевдокод представлен общий пример реализации Dispose(bool) в классе, который использует управляемые и машинные ресурсы.  
  
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