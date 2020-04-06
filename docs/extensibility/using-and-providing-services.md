---
title: Использование и предоставление услуг Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698736"
---
# <a name="using-and-providing-services"></a>Использование и предоставление служб
Услуга — это контракт между двумя VSPackages. Один VSPackage предлагает определенный набор интерфейсов для другого VSPackage потреблять. Например, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предлагает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> услугу любому VSPackage, который она загружает. Эта услуга <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> предоставляет интерфейс, который может быть использован для записи в журнал активности. Для получения дополнительной информации [см.](../extensibility/how-to-use-the-activity-log.md)

 VSPackages могут предложить свои услуги с помощью интерфейса. <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>

 Visual Studio предлагает важные услуги, такие как:

|Сервис IDE|Описание|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Предоставляет доступ к службам IDE, касающимся основных функциональных возможностей, VSPackages и реестра.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Обеспечивает основные функции, связанные с окнами и uI, в IDE, такие как возможность создания инструментов и окон документов.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Предоставляет основные функциональные возможности, связанные с решением, такие как возможность перечислять проекты, создавать новые проекты и контролировать изменения в проектах.|

## <a name="in-this-section"></a>В этом разделе
- [Основы обслуживания](../extensibility/internals/service-essentials.md) Представляет важные элементы сервиса Visual Studio.

- [Как: Получить услугу](../extensibility/how-to-get-a-service.md) Обсуждает, как запросить (потреблять) услугу.

- [Как: Предоставить услугу](../extensibility/how-to-provide-a-service.md) Обсуждает, как предоставить услугу.

- [Как: Обеспечить асинхронную услугу визуальной студии](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Обсуждает, как предоставить асинхронную услугу.

- [Как посмотреть на услуги по устранению неполадок](../extensibility/how-to-troubleshoot-services.md) Обсуждает общие проблемы и представляет их решения.

## <a name="related-sections"></a>Связанные разделы
- [Пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md)
