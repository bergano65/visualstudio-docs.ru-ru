---
title: Проекты вложения | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ec874d68b7a94811f0733f7045414cb48ddc880
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294259"
---
# <a name="nesting-projects"></a>Проекты вложения
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Разработчикам корпоративных приложений, которые используют пакет VS можно удобно Группировать схожие типы проектов вместе в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с помощью *проекта вложенности*. Например проект корпоративных шаблонов использует вложенные проекты в проекты группы на категории. Фасадной проекты, проекты веб-интерфейса и т. д., группируются вместе в одной категории.  
  
 В этом случае не ограничено число проектов, которые разработчик можно вложить в разделе каждого родительского проекта, несмотря на то, что разработчик может предоставить программным способом ограничения. Этот тип группирования также могут быть созданы рекурсивной, в этом случае проекты совпадает с типом дочернего проекта может быть вложен в узел дочерних станет подпроектом дочерний элемент, являющийся подпроект родительского элемента.  
  
 Вложенность проекта не является неотъемлемой частью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Необходимо написать код для включения вложения и подпроектом вложения в дочерние проекты. Родительский проект — это специальный пакет VSPackage, или тип проекта, создания и регистрации свой собственный идентификатор GUID, который содержит код, который требуется для реализации проекта вложения.  
  
 Пример вложенных проектов можно найти в примере Example.Nested проекта C#.  
  
## <a name="nested-projects-example"></a>Пример вложенных проектов  
 ![Вложенные решения проектов](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Пример вложенных проектов  
  
## <a name="see-also"></a>См. также  
 [Практическое: реализация вложенных проектов](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Рекомендации по выгрузке и перезагрузке вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Реализация обработки команд для вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Фильтрация диалогового окна AddItem для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Контрольный список: Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Параметры контекста](../../extensibility/internals/context-parameters.md)   
 [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)

