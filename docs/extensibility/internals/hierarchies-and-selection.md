---
title: Иерархии и выбор | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 741d61f4f3a62638e56aabb1f62f97aac4519d0c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596585"
---
# <a name="hierarchies-and-selection"></a>Иерархии и выбор
При настройке [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимо понимать как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] обрабатывает иерархии как проекты и как он использует контекст выбора, чтобы определить, будет отображаться для пользователя. В этом разделе рассматриваются основные понятия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] иерархии и выбор.

## <a name="in-this-section"></a>Содержание раздела
- [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Описывает проект иерархии и общий принцип иерархий.

- [Выбор и актуальность в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Описывает способ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) хранит сведения об объектах текущего активного пользователя и позволяет отслеживать валюты пакетов VSPackage.

- [Объекты контекста выбора](../../extensibility/internals/selection-context-objects.md)

 Обсуждается модель для как можно определить пользователя Выбор контекста фокус на окно.

- [Обратная связь с пользователем](../../extensibility/internals/feedback-to-the-user.md)

 Рассматриваются как функциональных возможностях доступным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] зависит от контекста текущего выделения и общем контексте интегрированной среды разработки пользователя.

## <a name="related-sections"></a>Связанные разделы
- [Архитектура типов проектов](../../extensibility/internals/project-types-architecture.md)

 Предоставляет подробные технические сведения о типах проектов.