---
title: Архитектура типов проектов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706322"
---
# <a name="project-types-architecture"></a>Архитектура типов проектов
Данный раздел содержит подробную информацию [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]об архитектуре типов проектов в .

## <a name="in-this-section"></a>В этом разделе
- [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)

 Перечисляет службы, которые может потреблять тип проекта, и интерфейсы, которые он должен реализовать.

- [Основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)

 Описывает типы интерфейсов проекта, которые необходимо реализовать и дополнительно реализовать для обеспечения дополнительной функциональности.

- [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)

 Помогает вам решить, когда необходимо создать тип проекта [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и когда вы можете использовать другую функцию расширяемости, такую как VSPackages и редакторы для достижения той же цели.

- [Иерархии и выбор](../../extensibility/internals/hierarchies-and-selection.md)

 Описывает, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] как использует иерархии и контекст выбора для обеспечения согласованного и упрощенного пользовательского интерфейса.

## <a name="related-sections"></a>Связанные разделы
- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)

 Объясняет, как подтипы проекта позволяют настроить [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] поведение [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]проектных систем и .

- [Типы проектов](../../extensibility/internals/project-types.md)

 Обеспечивает обзор проектов в качестве основных [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] строительных блоков интегрированной среды разработки (IDE). Ссылки предоставляются на дополнительные темы, объясняющие, как проекты контролируют строительство и компиляцию кода.
