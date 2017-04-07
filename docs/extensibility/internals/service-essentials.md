---
title: "Службы Essentials | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 8ff357d7ed3542a01cf8d98e36b9d0e99a122864
ms.lasthandoff: 04/05/2017

---
# <a name="service-essentials"></a>Essentials службы
Служба представляет собой контракт между двумя пакеты VSPackage. Один пакет VSPackage предоставляет определенный набор интерфейсов для другого пакета VSPackage для использования. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]сам является коллекцию пакетов VSPackage, предоставляющий службы для других пакетов VSPackage.  
  
 Например можно использовать службу SVsActivityLog для получения интерфейса IVsActivityLog, который можно использовать для записи в журнал действий. Дополнительные сведения см. в разделе [как: использование журнала действий](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]также предоставляет некоторые встроенные службы, которые не зарегистрированы. Пакеты VSPackage могут заменять встроенные или других служб, предоставляя переопределение службы. Для любой службы разрешена только одна служба переопределения.  
  
 Службы имеют не возможность обнаружения. Таким образом необходимо знать идентификатор службы (SID) службы, которую требуется использовать, и необходимо знать, какие интерфейсы он предоставляет. В справочной документации для службы предоставляет эти сведения.  
  
-   Пакеты VSPackage, предоставляющих службы, называются поставщиков услуг.  
  
-   Службы, предоставляемые для других пакетов VSPackage, называются глобальных служб.  
  
-   Службы, доступные только для реализующий их пакет VSPackage или к любому объекту, который создается, называются локальными службами.  
  
-   Службы, замените встроенных служб или служб, предоставляемых другими пакетами, называются переопределения службы.  
  
-   Службы или переопределения службы загружаются по запросу, то есть поставщик услуг загружается при запросе службы, которые он предоставляет с другим пакетом VSPackage.  
  
-   Для поддержки загрузки по требованию, поставщик услуг регистрирует глобальные службы в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [регистрации служб](../../misc/registering-services.md).  
  
-   После получения службой, используйте [QueryInterface](/cpp/atl/queryinterface) (неуправляемого кода) или явное приведение (управляемый код) для получения нужного интерфейса, например:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Управляемый код ссылается на службы путем его тип, в то время как неуправляемый код ссылается на службу по его идентификатору GUID.  
  
-   Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает пакет VSPackage, он передает поставщика услуг VSPackage для предоставления доступа VSPackage для глобальных служб. Это называется «размещение» VSPackage.  
  
-   Пакеты VSPackage могут быть поставщики для объектов, которые они создают. Например, формы может отправить запрос на обслуживание цвет его кадра, который может передать запрос к [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Управляемые объекты, которые глубокий уровень вложенности, или не размещен, может вызывать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>для прямого доступа к глобальных служб.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Дополнительные сведения см. в разделе [как: использование GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>См. также  
 [Список доступных служб](../../extensibility/internals/list-of-available-services.md)   
 [Использование и предоставления услуг](../../extensibility/using-and-providing-services.md)   
 [Приведение и преобразование типов](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Приведение](/cpp/cpp/casting)
