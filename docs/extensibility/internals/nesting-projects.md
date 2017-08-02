---
title: "Вложенность проектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Вложение проекта"
  - "вложенные проекты"
  - "проекты [Visual Studio SDK] дочерних проектов"
  - "проекты [Visual Studio SDK] вложение"
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Вложенность проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Разработчики приложений предприятия, использующие пакет VS удобно можно группировать похожих проектов вместе в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью *проекта вложенности*. Например корпоративный шаблон проекта используется вложенных проектов для проектов группы по категориям. Проекты фасадом, проекты веб\-интерфейса и так далее, группируются вместе в одной категории.  
  
 В этом сценарии не ограничено число проектов, которые разработчик можно вложить в каждый проект родительского несмотря на то, что разработчик может предоставить программным путем ограничения. Этот тип группирования можно также рекурсивной, в этом случае проекты того же типа как дочерний проект может быть вложен в дочерних станет подпроект дочернего, являющимся подпроектом родительского.  
  
 Вложение проекта не является неотъемлемой частью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Необходимо написать код для включения вложения и подпроекта вложения в дочерних проектов. Родительский проект — это специальные VSPackage, или тип проекта, созданных и зарегистрированных с собственный идентификатор GUID, который содержит код, который требуется для реализации проекта вложенности.  
  
 Пример вложенных проектов можно найти в образце Example.Nested проекта C\#.  
  
## Пример вложенных проектов  
 ![Вложенные решения проектов](~/extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Пример вложенных проектов  
  
## См. также  
 [Практическое руководство: реализации вложенных проектов](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Рекомендации по выгрузка и перезагрузка вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Реализация команды обработки вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Фильтрация AddItem диалоговым окном для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Контекстные параметры](../../extensibility/internals/context-parameters.md)   
 [Мастер \(. Файл VSZ\)](../../extensibility/internals/wizard-dot-vsz-file.md)