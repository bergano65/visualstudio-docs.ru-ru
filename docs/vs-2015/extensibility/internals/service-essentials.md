---
title: Службы Essentials | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec9ccc92a8650c71336fc4a6916b797bd449dc7a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178142"
---
# <a name="service-essentials"></a>Основные компоненты службы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Служба представляет собой контракт между двух пакетов VSPackage. Один пакет VSPackage предоставляет ряд интерфейсов для другого пакета VSPackage для использования. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] сам является коллекцию пакетов VSPackage, предоставляющий службы для других пакетов VSPackage.  
  
 Например можно использовать службу SVsActivityLog получить интерфейс IVsActivityLog, который можно использовать для записи в журнал действий. Дополнительные сведения см. в разделе [как: использование журнала действий](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] также предоставляет некоторые встроенные службы, которые не зарегистрированы. Пакеты VSPackage можно заменить встроенные или других служб, предоставляя переопределение службы. Для любой службы разрешена только одна служба переопределения.  
  
 Службы имеют нет возможности обнаружения. Таким образом необходимо знать идентификатор службы (SID) службы, который вы хотите использовать, и необходимо знать, какие интерфейсы он предоставляет. В справочной документации для службы предоставляет эти сведения.  
  
-   Пакеты VSPackage, предоставляющих службы, называются поставщиков услуг.  
  
-   Службы, предоставляемые для других пакетов VSPackage, называются глобальных служб.  
  
-   Службы, которые доступны только для реализующий их пакет VSPackage, или к любому объекту, которые оно создает, называются локальными службами.  
  
-   Службы, которые заменяют встроенные службы или служб, предоставляемых другими пакетами, называются переопределения службы.  
  
-   Службы или переопределения службы, они загружаются по требованию, то есть, поставщик услуг загружается при запросе службы, предоставляемые им в другом пакете VSPackage.  
  
-   Для поддержки загрузки по требованию, поставщик услуг регистрирует глобальные службы в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [регистрация служб](../../misc/registering-services.md).  
  
-   После получения службы, используйте [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (неуправляемый код) или приведения (управляемый код) для получения требуемого интерфейса, например:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Управляемый код ссылается на службу по его типу, тогда как неуправляемый код ссылается на службу по его идентификатору GUID.  
  
-   Когда [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] загружает VSPackage, он передает поставщик служб VSPackage для предоставления доступа VSPackage для глобальных служб. Это называется «размещение» VSPackage.  
  
-   Пакеты VSPackage могут быть поставщики услуг для объектов, которые они создают. Например, формы может отправить запрос на обслуживание цвет фреймом, который может передан запрос [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   Управляемые объекты, которые глубоко вложенных или не найдено, может вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для прямого доступа к глобальных служб. Дополнительные сведения см. в разделе [как: использование GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>См. также  
 [Список доступных служб](../../extensibility/internals/list-of-available-services.md)   
 [Использование и предоставление служб](../../extensibility/using-and-providing-services.md)   
 [Приведение и преобразование типов](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Приведение](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)

