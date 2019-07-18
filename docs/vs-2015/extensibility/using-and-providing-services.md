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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177442"
---
# <a name="using-and-providing-services"></a>Использование и предоставление служб
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Служба представляет собой контракт между двух пакетов VSPackage. Один пакет VSPackage предоставляет определенный набор интерфейсов для другого пакета VSPackage для использования. Например [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предлагает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службы любой пакет VSPackage он загружает. Эта служба предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который может использоваться для записи в журнал действий. Дополнительные сведения см. в разделе [Практическое руководство. Использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
 Пакеты VSPackage может предложить службы с помощью среды <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> интерфейс...  
  
 Visual Studio предлагает важных служб, таких как следующие:  
  
|Интегрированная среда разработки службы|Описание|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Предоставляет доступ к интегрированной среде разработки служб работы с основные функциональные возможности, VSPackages и реестром.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет базовые Оконные функции и функции, связанные с пользовательского интерфейса в интегрированной среде разработки, такие как возможность создания средств и окон документов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Обеспечивает базовые функции, связанные с решением, такие как возможность перечислить проекты, создание новых проектов и отслеживать изменения в проект.|  
  
## <a name="in-this-section"></a>В этом разделе  
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)  
 Представляет важных элементов службы Visual Studio.  
  
 [Практическое руководство. Получение службы](../extensibility/how-to-get-a-service.md)  
 Описывается запрос (использовать) службы.  
  
 [Практическое руководство. Предоставление службы](../extensibility/how-to-provide-a-service.md)  
 Описывает, как для предоставления службы.  
  
 [Практическое руководство. Предоставление асинхронной службы Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Описание способов предоставить асинхронные службы.  
  
 [Практическое руководство. Устранение неполадок, связанных со службами](../extensibility/how-to-troubleshoot-services.md)  
 Описание распространенных проблем и представляет их решения.  
  
## <a name="related-sections"></a>Связанные разделы  
 [SDK для Visual Studio](../extensibility/visual-studio-sdk.md)
