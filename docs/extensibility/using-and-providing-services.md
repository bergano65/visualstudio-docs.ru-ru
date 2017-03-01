---
title: "Использование и предоставления услуг | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 41
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fb380330420d6256190ade75e0afe89f8cbda303
ms.lasthandoff: 02/22/2017

---
# <a name="using-and-providing-services"></a>Использование и предоставления услуг
Служба представляет собой контракт между двумя VSPackages. Один VSPackage предлагает ряд интерфейсов для другой VSPackage для использования. Например [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предлагает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>обслуживание для любой VSPackage загружает.</xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Эта служба предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>интерфейс, который может использоваться для записи в журнал действий.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Дополнительные сведения см. в разделе [Практическое руководство: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
 Пакеты VSPackage может предложить собственные службы с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>интерфейса...</xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>  
  
 Visual Studio предлагает важные услуги, например следующие:  
  
|Служба интегрированной среды разработки|Описание|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Предоставляет доступа к интегрированной среды разработки служб работы с базовую функциональность, пакеты VSPackage и реестра.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет основных операций с окнами и функции, связанные с пользовательского интерфейса в Интегрированной среде разработки, например возможность создавать средства и окна документов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Обеспечивает базовые функции, связанные с решением, такие как возможность перечислить проекты, создание новых проектов и отслеживать изменения в проект.|  
  
## <a name="in-this-section"></a>Содержание  
 [Основы службы](../extensibility/internals/service-essentials.md)  
 Представляется важных элементов службы Visual Studio.  
  
 [Практическое руководство: Получение службы](../extensibility/how-to-get-a-service.md)  
 Описывает, как запросить (использовать) службы.  
  
 [Практическое руководство: предоставления службы](../extensibility/how-to-provide-a-service.md)  
 Описывает способ предоставления службы.  
  
 [Практическое руководство: предоставить службы асинхронной Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Описывает, как для обеспечения асинхронной службе.  
  
 [Практическое руководство: Устранение неполадок служб](../extensibility/how-to-troubleshoot-services.md)  
 Описание распространенных проблем и представляет их решения.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md)
