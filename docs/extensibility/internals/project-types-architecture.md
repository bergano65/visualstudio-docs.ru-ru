---
title: "Архитектура типы проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86ff1ed0b616eb52d57755e7537642e4f086c1f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="project-types-architecture"></a>Архитектура типы проектов
Этот раздел содержит подробные сведения об архитектуре типов проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Содержание  
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