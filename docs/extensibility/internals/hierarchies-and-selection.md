---
title: Иерархии и выбор | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d59a5160b5c20a3243426eaf1fda4b72e58e93
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328869"
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