---
title: Практическое руководство. Использование GetGlobalService | Документация Майкрософт
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054371"
---
# <a name="how-to-use-getglobalservice"></a>Практическое руководство. Использование GetGlobalService
Иногда может потребоваться доступ к службе из окна инструментов или контейнер, который не был помещен в узел, в противном случае размещения с поставщиком услуг, не знает о службу, которую вы хотите управлять. Например может потребоваться запись в журнале действий в элементе управления. Дополнительные сведения об этих и других сценариев см. в разделе [как: Устранение неполадок в службах](../extensibility/how-to-troubleshoot-services.md).  
  
 Вы можете получить большинство [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] службы путем вызова статического <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> полагается на поставщик кэшированных служб, который инициализируется первый раз, любой пакет VSPackage на основе <xref:Microsoft.VisualStudio.Shell.Package> помещен в узел. Вы должны гарантировать, что это условие выполнено, в противном случае будьте готовы к услуга null.  
  
 К счастью <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> правильно работает в большинстве случаев.  
  
- Если пакет VSPackage предоставляет службу, известного только другом пакете VSPackage, VSPackage, запрашивающего службу размещен перед VSPackage, предоставляющий, что загружены службы.  
  
- Если окно инструментов создается пакетом VSPackage, VSPackage задан до создания окна инструментов.  
  
- Если контейнер элемента управления размещается в окна инструментов, созданного пакетом VSPackage, VSPackage задан до создания контейнера элемента управления.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Чтобы получить службу в контейнере инструментов окна или элемента управления  
  
- Вставьте этот код в конструкторе, окно инструментов или контейнер элемента управления:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Этот код получает службу SVsActivityLog и приводит его к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который может использоваться для записи в журнал действий. Пример см. в статье [Практическое руководство. Использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Устранение неполадок служб](../extensibility/how-to-troubleshoot-services.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)