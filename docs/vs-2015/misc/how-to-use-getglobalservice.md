---
title: Как использовать GetGlobalService | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948186"
---
# <a name="how-to-use-getglobalservice"></a>Практическое руководство. Использование GetGlobalService
Иногда может потребоваться получить службу из окна инструментов или контейнера элемента управления, который не был добавлен в узел, или в другом месте с поставщиком услуг, который не знает о нужной службе. Например, может потребоваться запись в журнал действий из элемента управления. Дополнительные сведения об этих и других сценариях см. [в разделе руководство. Устранение неполадок служб](../extensibility/how-to-troubleshoot-services.md).  
  
 Большинство служб можно получить [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , вызвав статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> полагается на кэшированный поставщик служб, который инициализируется в первый раз, когда любой из VSPackage, производный от <xref:Microsoft.VisualStudio.Shell.Package> , находится на сайте. Необходимо убедиться в том, что это условие выполнено, или, в противном случае, быть подготовленным для службы со значением NULL.  
  
 К счастью, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> большая часть времени работает правильно.  
  
- Если пакет VSPackage предоставляет службу, известную только для другого пакета VSPackage, то пакет VSPackage, запрашивающий службу, будет находиться на сайте до загрузки пакета VSPackage, предоставляющего службу.  
  
- Если окно инструментов создается пакетом VSPackage, то перед созданием окна инструментов VSPackage размещается в узле.  
  
- Если контейнер элемента управления размещается в окне инструментов, созданном с помощью VSPackage, то пакет VSPackage размещается до создания контейнера элемента управления.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Получение службы из окна инструментов или с помощью контейнера элементов управления  
  
- Вставьте этот код в конструктор, окно инструментов или контейнер элемента управления:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Этот код получает службу Свсактивитилог и приводит ее к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейсу, который можно использовать для записи в журнал действий. Пример см. в разделе [как использовать журнал действий](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>См. также:  
 [Руководство. Устранение неполадок служб](../extensibility/how-to-troubleshoot-services.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)