---
title: "Добавление проекта и шаблоны элементов проекта | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "проекты [Visual Studio SDK], добавление"
  - "Добавление элементов проекта [Visual Studio]"
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Добавление проекта и шаблоны элементов проекта
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

При создании собственных типов проектов необходимо обеспечить поддержку для добавления новых проектов и элементов проектов с помощью стандартных [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диалоговые окна интегрированной среды разработки \(ide\).  В следующих подразделах обсуждаются различные методы для добавления проектов и элементов проектов.  
  
## В этом подразделе  
 [Контекст проекта](../../extensibility/internals/project-context.md)  
 Объясняет, что проект содержит большую часть данных о контексте для которых испаряется среды.  
  
 [Приоритет проекта](../../extensibility/internals/project-priority.md)  
 Объясняет, что элемент проекта обычно член одного проекта помочь избежать неоднозначности о которой используется проект открыть элемент.  
  
 [Проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md)  
 Предоставляет сведения о 2 типах редакторов, которые можно использовать для открытия файлов в проекте и проект роль играет в определение, являющийся редактором для использования при открытии элемента проекта.  
  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)  
 Объясняет, что происходит, когда a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проект создан.  
  
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Объясняет процесс добавления элементов в **Добавление нового элемента** диалоговое окно.  
  
 [Добавление папки в диалоговом окне Новый проект](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Пример зарегистрировать новый каталог, содержащий пользовательские шаблоны, доступные VSPackage.  
  
 [Добавление каталогов, чтобы добавить новый элемент\-диалоговое окно](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Пример новый набор каталогов для регистрации **Добавление нового элемента** диалоговое окно.  
  
 [Команды, определенные в интегрированной среде разработки, для расширения системы проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Перечисляет различные типы элементов команд, используемых для расширения системы проектов.  
  
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Перечисляет CATIDs для объектов, которые используются для расширения [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]"  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] системы проектов.  
  
## Связанные подразделы  
 [Практическое руководство: открытие редакторов конкретного проекта](../../extensibility/how-to-open-project-specific-editors.md)  
 Содержит пошаговые инструкции по открытию элемент подсистемы привязанный к конкретным редактором для проекта.  
  
 [Практическое руководство: Откройте стандартные редакторы](../../extensibility/how-to-open-standard-editors.md)  
 Содержит пошаговые инструкции по открытию стандартный редактор.  
  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)  
 Ссылки на разделы подтипа проекта на концептуальные.  Подтипы проекта расширяют существовать [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проекты.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Ссылки на дополнительные разделы, которые предоставляют сведения о том, как создавать новые типы проектов.