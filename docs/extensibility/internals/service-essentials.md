---
title: "Основы службы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "службы, essentials"
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Основы службы
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Служба представляет собой контракт между двумя VSPackages. Один VSPackage предоставляет ряд интерфейсов для другой VSPackage для использования.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сам является коллекция пакеты VSPackage, который предоставляет службы для других пакетов VSPackages.  
  
 Например можно использовать службу SVsActivityLog для получения интерфейса IVsActivityLog, который можно использовать для записи в журнал действий. Для получения дополнительной информации см. [Практическое руководство: использование журнала действий](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] также предоставляет некоторые встроенные службы, которые не зарегистрированы. Пакеты VSPackage можно заменить встроенные и другие службы, предоставляя переопределение службы. Для любой службы разрешена только одна служба переопределение.  
  
 Службы имеют нет возможность обнаружения. Таким образом необходимо знать идентификатор службы \(SID\) службы, которую требуется использовать, и необходимо знать, какие интерфейсы он предоставляет. Справочная документация для службы предоставляет эти сведения.  
  
-   Пакеты VSPackage, предоставляющие службы называются поставщиков услуг.  
  
-   Службы, предоставляемые для других пакетов VSPackages называются глобальных служб.  
  
-   Службы, которые доступны только в VSPackage, реализующий их, или к любому объекту, который создается, называются локальными службами.  
  
-   Службы, замена встроенных служб или служб, предоставляемых другими пакетами, называются переопределения службы.  
  
-   Службы или переопределения службы загружаются по требованию, то есть поставщик услуг загружается при запросе службы, предоставляемые с другой VSPackage.  
  
-   Для поддержки загрузки по требованию, поставщик услуг регистрирует глобальных служб с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Для получения дополнительной информации см. [Регистрация служб](../../misc/registering-services.md).  
  
-   После получения службы, используйте [QueryInterface](/visual-cpp/atl/queryinterface) \(неуправляемый код\) или приведение \(управляемый код\) для получения нужного интерфейса, например:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Управляемого кода относится к службе по его типу, тогда как неуправляемый код ссылается на службу по его идентификатору GUID.  
  
-   Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает VSPackage, он передает поставщику служб VSPackage, чтобы предоставить доступ VSPackage для глобальных служб. Это называется «размещение» VSPackage.  
  
-   Пакеты VSPackage может быть поставщиков услуг для объектов, которые они создают. Например, формы может отправить запрос на обслуживание цвет его кадра, который может передать запрос для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Управляемые объекты, глубокий уровень вложенности, или не размещен, может вызывать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для прямого доступа к глобальных служб. Для получения дополнительной информации см. [Практическое руководство. Использование GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## См. также  
 [Список доступных служб](../../extensibility/internals/list-of-available-services.md)   
 [Использование и предоставления услуг](../../extensibility/using-and-providing-services.md)   
 [Приведение и преобразование типов](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Приведение](/visual-cpp/cpp/casting)