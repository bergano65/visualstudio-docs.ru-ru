---
title: Архитектура типы проектов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6ef7fe6fbf4a8899606dca35c10745e68e3cbfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="project-types-architecture"></a>Архитектура типы проектов
Этот раздел содержит подробные сведения об архитектуре типов проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)  
 Список служб, которые могут использовать тип проекта и интерфейсы, которые он должен реализовать.  
  
 [Основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)  
 Описываются интерфейсы, типы проектов необходимо реализовать и при необходимости можно реализовать дополнительные функциональные возможности.  
  
 [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)  
 Введите помогает решить, когда необходимо создать проект и когда можно использовать другой [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] возможность расширения, такие как пакеты VSPackage и редакторы для достижения общей цели.  
  
 [Иерархии и выбор](../../extensibility/internals/hierarchies-and-selection.md)  
 Описывает способ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует для взаимодействия с пользователями, согласованное и упрощенный иерархии и выделенный фрагмент.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)  
 Объясняет, как подтипы проекта позволяют настраивать поведение системы проектов из [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Общие сведения о проектах как основных стандартных блоках [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Приводятся ссылки на дополнительные разделы, в которых объясняется, как проекты контролировать создание и компиляция кода.