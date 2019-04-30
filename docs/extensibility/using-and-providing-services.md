---
title: Использование и предоставление служб | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36f49d4e1ebaa6d8e15e43b821af56204739cb07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62798975"
---
# <a name="using-and-providing-services"></a>Использование и предоставление служб
Служба представляет собой контракт между двух пакетов VSPackage. Один пакет VSPackage предоставляет определенный набор интерфейсов для другого пакета VSPackage для использования. Например [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предлагает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службы любой пакет VSPackage он загружает. Эта служба предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который может использоваться для записи в журнал действий. Дополнительные сведения см. в разделе [Как Использование журнала действий](../extensibility/how-to-use-the-activity-log.md).

 Пакеты VSPackage может предложить службы с помощью среды <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> интерфейс...

 Visual Studio предлагает важных служб, таких как следующие:

|Интегрированная среда разработки службы|Описание|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Предоставляет доступ к интегрированной среде разработки служб работы с основные функциональные возможности, VSPackages и реестром.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет базовые Оконные функции и функции, связанные с пользовательского интерфейса в интегрированной среде разработки, такие как возможность создания средств и окон документов.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Обеспечивает базовые функции, связанные с решением, такие как возможность перечислить проекты, создание новых проектов и отслеживать изменения в проект.|

## <a name="in-this-section"></a>В этом разделе
- [Основные компоненты службы](../extensibility/internals/service-essentials.md) представляется важных элементов службы Visual Studio.

- [Практическое руководство. Доступ к службе](../extensibility/how-to-get-a-service.md) описывается запрос (использовать) службы.

- [Практическое руководство. Предоставляет службу](../extensibility/how-to-provide-a-service.md) описывает, как для предоставления службы.

- [Практическое руководство. Предоставить асинхронной службы Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Описание способов предоставить асинхронные службы.

- [Практическое руководство. Устранение неполадок в службах](../extensibility/how-to-troubleshoot-services.md) обсуждаются распространенные проблемы и представляет их решения.

## <a name="related-sections"></a>Связанные разделы
- [SDK для Visual Studio](../extensibility/visual-studio-sdk.md)