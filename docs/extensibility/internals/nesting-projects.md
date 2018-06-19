---
title: Проекты вложение | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35d0f4f8906acc08733894d1c24b6d8c2199e1f7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131164"
---
# <a name="nesting-projects"></a>Вложенность проектов
Разработчики приложений предприятия, использующие пакет VS удобным образом можно группировать схожие типы проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью *проекта вложенности*. Например проект шаблона предприятия использует вложенных проектов для проектов группы по категориям. Проекты оболочкой, проекты веб-интерфейса и так далее, группируются вместе в одной категории.  
  
 В этом сценарии не ограничено число проектов, которые разработчик могут быть вложены в каждый родительский проект, несмотря на то, что разработчик может предоставить программным путем ограничения. Этот тип группирования могут также задаваться рекурсивной, в этом случае проекты того же типа как дочерний проект может быть вложен в узел дочерних станут подпроектом дочернего элемента, являющимся подпроектом родительского элемента.  
  
 Вложение проекта не является неотъемлемой частью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Необходимо написать код, чтобы включить вложения и подпроекта вложения в дочерних проектов. Родительский проект — это специальные VSPackage, или тип проекта создан и зарегистрирован с собственный идентификатор GUID, который содержит код, который требуется для реализации проекта вложение.  
  
 Пример вложенных проектов можно найти в образце Example.Nested проекта C#.  
  
## <a name="nested-projects-example"></a>Пример вложенных проектов  
 ![Вложенные решения проектов](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Пример вложенных проектов  
  
## <a name="see-also"></a>См. также  
 [Как: реализации вложенных проектов](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Рекомендации по выгрузка и перезагрузка проектов вложенные](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Реализация команды обработки вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Фильтрация AddItem диалоговым окном для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Контекстные параметры](../../extensibility/internals/context-parameters.md)   
 [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)