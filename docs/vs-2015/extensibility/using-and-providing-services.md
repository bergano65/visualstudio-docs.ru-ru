---
title: Использование и предоставление служб | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f58e29797e9a7760aa0f48c68868199f51b3c92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177442"
---
# <a name="using-and-providing-services"></a>Использование и предоставление служб
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Служба — это контракт между двумя пакетами VSPackage. Один пакет VSPackage предлагает конкретный набор интерфейсов для использования другим пакетом VSPackage. Например, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службу для любого пакета VSPackage, который она загружает. Эта служба предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который можно использовать для записи в журнал действий. Дополнительные сведения см. в разделе [инструкции. Использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
 Пакеты VSPackage могут предоставлять собственные службы с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> интерфейса.  
  
 Visual Studio предлагает следующие важные службы:  
  
|Служба IDE|Описание|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Предоставляет доступ к службам IDE, которые работают с базовой функциональностью, пакеты VSPackage и реестр.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет основные функциональные возможности для работы с окнами и интерфейсом пользователя в интегрированной среде разработки, например возможность создания средств и окон документов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Предоставляет базовые функции, связанные с решениями, такие как возможность перечисления проектов, создания новых проектов и наблюдения за изменениями проекта.|  
  
## <a name="in-this-section"></a>в этом разделе  
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)  
 Представляет важные элементы службы Visual Studio.  
  
 [Практическое руководство. Получение службы](../extensibility/how-to-get-a-service.md)  
 Описывает, как запросить (использовать) службу.  
  
 [Практическое руководство. Предоставление службы](../extensibility/how-to-provide-a-service.md)  
 Описывает, как предоставить службу.  
  
 [Практическое руководство. Предоставление асинхронной службы Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Описывает, как предоставить асинхронную службу.  
  
 [Практическое руководство. Устранение неполадок, связанных со службами](../extensibility/how-to-troubleshoot-services.md)  
 Обсуждаются распространенные проблемы и предоставляются их решения.  
  
## <a name="related-sections"></a>См. также  
 [SDK для Visual Studio](../extensibility/visual-studio-sdk.md)
