---
title: Иерархии и выбор | Документация Майкрософт
description: Узнайте, как Visual Studio обрабатывает иерархии, такие как проекты, и как она использует контекст выбора для определения того, что отображается пользователю.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98f3dcfa73387f2b90ed829df198d3e9f0ccb2ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880061"
---
# <a name="hierarchies-and-selection"></a>Иерархии и выбор
При настройке необходимо [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] понимать, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] обрабатывает иерархии, такие как проекты, и как она использует контекст выбора для определения того, что отображается пользователю. В этом разделе обсуждаются концепции [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] иерархий и выбора.

## <a name="in-this-section"></a>Содержание раздела
- [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Описывает иерархии проектов и общую концепцию иерархий.

- [Выбор и валюта в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Описывает, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированная среда разработки (IDE) поддерживает информацию о текущих активных объектах пользователя и позволяет VSPackage фиксировать валюту.

- [Объекты контекста выделения](../../extensibility/internals/selection-context-objects.md)

 Обсуждается модель того, как можно определить фокус контекста выбора пользователя в окне.

- [Отзыв пользователю](../../extensibility/internals/feedback-to-the-user.md)

 Описывает, как доступные функциональные возможности в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] основаны на текущем контексте выбора пользователя и общем контексте интегрированной среды разработки.

## <a name="related-sections"></a>Связанные разделы
- [Архитектура типов проектов](../../extensibility/internals/project-types-architecture.md)

 Содержит подробные технические сведения о типах проектов.
