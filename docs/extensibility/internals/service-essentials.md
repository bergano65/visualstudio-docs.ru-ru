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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0b78b5f9bf1fb6d9c92657b99e6d21b58cab2728
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

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
  
-   Для поддержки загрузки по требованию, поставщик услуг регистрирует глобальные службы в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [как: обслуживать](../../extensibility/how-to-provide-a-service.md).  
  
-   После получения службой, используйте [QueryInterface](/cpp/atl/queryinterface) (неуправляемого кода) или явное приведение (управляемый код) для получения нужного интерфейса, например:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    ```  
  
-   Управляемый код ссылается на службы путем его тип, в то время как неуправляемый код ссылается на службу по его идентификатору GUID.  
  
-   Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает пакет VSPackage, он передает поставщика услуг VSPackage для предоставления доступа VSPackage для глобальных служб. Это называется «размещение» VSPackage.  
  
-   Пакеты VSPackage могут быть поставщики для объектов, которые они создают. Например, формы может отправить запрос на обслуживание цвет его кадра, который может передать запрос к [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Управляемые объекты, которые глубокий уровень вложенности, или не размещен, может вызывать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для прямого доступа к глобальных служб.   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>Использование GetGlobalService  
  
Иногда может потребоваться доступ к службе из окна инструментов или контейнер, в котором не размещен, иначе размещения у поставщика услуг, не знает о службу, которую вы хотите управлять. Например может потребоваться запись в журнал действий в элементе управления. Дополнительные сведения об этих и других сценариев см. в разделе [как: Устранение неполадок службы](../../extensibility/how-to-troubleshoot-services.md).  
  
Большинство служб Visual Studio можно получить путем вызова статического <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод.  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>использует кэшированные службе задан поставщик, который инициализируется первый раз, любой VSPackage на основе пакета. Необходимо гарантировать, что это условие выполнено, иначе наберитесь null службы.  
  
К счастью <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> правильно работает в большинстве случаев.  
  
-   Если пакет VSPackage предоставляет службу, известные только в другом пакете VSPackage, VSPackage, запрашивающего службу размещении перед VSPackage, при условии, что загружен.  
  
-   Если окно инструментов создается пакетом VSPackage, VSPackage задан до создания окна инструментов.  
  
-   Если контейнер элемента управления размещен в окно инструментов, созданные VSPackage, VSPackage размещении перед созданием контейнера элемента управления.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Чтобы получить службу в контейнер средство окна или элемента управления  
  
-   Вставьте этот код в конструкторе, окна инструментов или контейнер элемента управления:  
  
    ```csharp  
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```  
    ```vb  
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```  
    
    Этот код получает службу SVsActivityLog и приводит его к IVsActivityLog интерфейс, который может использоваться для записи в журнал действий. Пример см. в разделе [как: использование журнала действий](../../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>См. также  
 [Список доступных служб](../../extensibility/internals/list-of-available-services.md)   
 [Использование и предоставления услуг](../../extensibility/using-and-providing-services.md)   
 [Приведение и преобразование типов](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Приведение](/cpp/cpp/casting)
