---
title: "CA1063: следует правильно реализовывать IDisposable | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ImplementIDisposableCorrectly"
  - "CA1063"
helpviewer_keywords: 
  - "CA1063"
  - "ImplementIDisposableCorrectly"
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1063: следует правильно реализовывать IDisposable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 `IDisposable` реализован неправильно.  Далее перечислены некоторые возможные причины данной проблемы.  
  
-   IDisposable повторно реализован в классе.  
  
-   Метод "Finalize" переопределен.  
  
-   Метод "Dispose" переопределен.  
  
-   "Dispose\(\)" не является открытым, запечатанным или не имеет имя "Dispose".  
  
-   "Dispose\(bool\)" является незащищенным, виртуальным или незапечатанным.  
  
-   В незапечатанных типах "Dispose\(\)" должен вызывать "Dispose\(true\)".  
  
-   В незапечатанных типах реализация метода "Finalize" не вызывает ни метод "Dispose\(bool\)", ни метод завершения класса.  
  
 Нарушение любого из этих шаблонов приведет к выводу предупреждения.  
  
 Каждый незапечатанный корневой тип IDisposable должен предоставлять собственный виртуальный метод Dispose\(bool\) с типом void.  Метод "Dispose\(\)" должен вызывать "Dipose\(true\)", а метод "Finalize" — "Dispose\(false\)".  При создании незапечатанного корневого типа IDisposable необходимо определить метод "Dispose\(bool\)" и вызывать его.  Дополнительные сведения см. в подразделе [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md) раздела [Рекомендации по проектированию Framework](../Topic/Framework%20Design%20Guidelines.md) документации по .NET Framework.  
  
## Описание правила  
 Все типы IDisposable должны правильно реализовывать шаблон "Dispose".  
  
## Устранение нарушений  
 Проверьте код и выберите решение, подходящее для устранения нарушения.  
  
-   Удалите IDisposable из списка интерфейсов, реализованных с помощью {0} и переопределите базовый класс реализации "Dispose".  
  
-   Удалите метод завершения из типа {0}, переопределите метод "Dispose\(bool disposing\)" и поместите логику завершения в путь к коду, где "disposing" имеет значение "false".  
  
-   Удалите {0}, переопределите метод "Dispose\(bool disposing\)" и поместите логику dispose в путь к коду, где "disposing" имеет значение "false".  
  
-   Убедитесь, что {0} объявлен как открытый и запечатанный.  
  
-   Переименуйте {0} на "Dispose" и убедитесь, что он объявлен как открытый и запечатанный.  
  
-   Убедитесь, что {0} объявлен как защищенный, виртуальный и распечатанный.  
  
-   Измените {0} так, чтобы он вызывал метод "Dispose\(true\)", затем метод "GC.SuppressFinalize" в экземпляре текущего объекта \("this" или "Me" в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), а затем возвращал результат.  
  
-   Измените {0} так, чтобы он вызывал метод "Dispose\(false\)", а затем возвращался.  
  
-   При написании незапечатанного корневого класса IDisposable убедитесь, что реализация IDisposable выполняется в соответствии с описанным выше шаблоном.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример псевдокода  
 В следующем псевдокоде представлен общий пример реализации метода "Dispose\(bool\)" в классе, использующем управляемые и собственные ресурсы.  
  
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