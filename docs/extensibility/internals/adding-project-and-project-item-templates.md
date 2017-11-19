---
title: "Добавление проекта и шаблоны проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0201d2f282365a028b6251324b07276c995621ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="adding-project-and-project-item-templates"></a>Добавление в проект и шаблоны элементов проекта
При создании собственных типов проекта должно обеспечивать поддержку для добавления новых проектов и элементов проекта с помощью стандартной [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интеграции диалоговые окна Интегрированной среде разработки. В следующих разделах рассматриваются различные методы для добавления проектов и элементов проектов.  
  
## <a name="in-this-section"></a>Содержание  
 [Контекст проекта](../../extensibility/internals/project-context.md)  
 Объясняет, что проект предоставляет большую часть сведений о контексте для процесс в среде.  
  
 [Приоритет проекта](../../extensibility/internals/project-priority.md)  
 Объясняет, что элемент проекта обычно является членом один проект, чтобы избежать неоднозначности, о том, какие проект используется, чтобы открыть элемент.  
  
 [Проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md)  
 Предоставляет сведения об этих двух типах редакторов, которые могут использоваться для открытия файлов в проекте и в роли проекта играет в определении редактора для использования при открытии элемента проекта.  
  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)  
 Описание операций, происходящих при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] создается проект.  
  
 [Добавление элементов в диалоговые окна "Добавление новых элементов"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Описание процесса добавления элементов **Добавление нового элемента** диалоговое окно.  
  
 [Добавление каталогов в диалоговое окно "Создание проекта"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Предоставляет пример регистрации новый каталог, содержащий пользовательские шаблоны, становится доступным в результате VSPackage.  
  
 [Добавление каталогов в диалоговое окно "Добавление новых элементов"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Предоставляет пример новый набор каталогов для регистрации **Добавление нового элемента** диалоговое окно.  
  
 [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Список различных типов элементов команды, используемые для расширения системы проектов.  
  
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Перечисляет CATID для объектов, которые используются для расширения [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] систем проекта.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Практическое руководство. Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)  
 Содержит пошаговые инструкции по открытию элемент само по себе привязан к определенным редактором для проекта.  
  
 [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)  
 Содержит пошаговые инструкции по открытию стандартного редактора.  
  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)  
 Ссылки на концептуальные разделы подтип проекта. Подтипы проекта расширять существующие [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проекты.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Ссылки на дополнительные разделы, которые содержат сведения о создании новых типов проектов.