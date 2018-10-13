---
title: 'Практическое: использование GetGlobalService | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: 5ce0d5657fa65cd727da2b97b3dd24735a81937a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276134"
---
# <a name="how-to-use-getglobalservice"></a>Практическое руководство. Использование GetGlobalService
Иногда может потребоваться доступ к службе из окна инструментов или контейнер, который не был помещен в узел, в противном случае размещения с поставщиком услуг, не знает о службу, которую вы хотите управлять. Например может потребоваться запись в журнале действий в элементе управления. Дополнительные сведения об этих и других сценариев см. в разделе [как: Устранение неполадок службы](../extensibility/how-to-troubleshoot-services.md).  
  
 Вы можете получить большинство [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] службы путем вызова статического <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> полагается на поставщик кэшированных служб, который инициализируется первый раз, любой пакет VSPackage на основе <xref:Microsoft.VisualStudio.Shell.Package> помещен в узел. Вы должны гарантировать, что это условие выполнено, в противном случае будьте готовы к услуга null.  
  
 К счастью <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> правильно работает в большинстве случаев.  
  
-   Если пакет VSPackage предоставляет службу, известного только другом пакете VSPackage, VSPackage, запрашивающего службу размещен перед VSPackage, предоставляющий, что загружены службы.  
  
-   Если окно инструментов создается пакетом VSPackage, VSPackage задан до создания окна инструментов.  
  
-   Если контейнер элемента управления размещается в окна инструментов, созданного пакетом VSPackage, VSPackage задан до создания контейнера элемента управления.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Чтобы получить службу в контейнере инструментов окна или элемента управления  
  
-   Вставьте этот код в конструкторе, окно инструментов или контейнер элемента управления:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Этот код получает службу SVsActivityLog и приводит его к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который может использоваться для записи в журнал действий. Например, см. в разделе [как: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>См. также  
 [Практическое: Устранение неполадок в службах](../extensibility/how-to-troubleshoot-services.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)