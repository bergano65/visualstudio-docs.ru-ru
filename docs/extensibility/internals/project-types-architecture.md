---
title: Архитектура типов проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3aee42e266e1082228c30ce56ac128e19ef6c576
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909464"
---
# <a name="project-types-architecture"></a>Архитектура типов проектов
Этот раздел содержит подробные сведения об архитектуре типов проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>В этом разделе
- [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)

 Список служб, которые могут использовать тип проекта и интерфейсы, которые он должен реализовать.

- [Основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)

 Описываются интерфейсы, типы проектов необходимо реализовать и при необходимости можно реализовать дополнительные функциональные возможности.

- [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)

 Введите помогает решить, когда необходимо создать проект и когда можно использовать другой [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] возможность расширения, такие как пакеты VSPackage и редакторов для достижения той же цели.

- [Иерархии и выбор](../../extensibility/internals/hierarchies-and-selection.md)

 Описывает способ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует для работы согласованный и упрощенный пользовательский иерархии и контекст выделения.

## <a name="related-sections"></a>Связанные разделы
- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)

 Объясняет, как подтипов проекта позволяют настраивать поведение системы проектов из [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

- [Типы проектов](../../extensibility/internals/project-types.md)

 Общие сведения о проектах как основные стандартные блоки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Приведены ссылки на дополнительные разделы, в которых объясняется, как управлять проектами, создания и компиляции кода.