---
title: "Фильтрация AddItem диалоговым окном для вложенных проектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Фильтрация вложенных проектов"
  - "вложенные проекты, диалоговое окно AddItem поле фильтрации"
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Фильтрация AddItem диалоговым окном для вложенных проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

При отображении AddItem диалоговое окно для вложенных проекта родительский проект может отслеживать, какие элементы отображаются в диалоговом окне.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> интерфейс позволяет фильтровать узлы, которые будут включены в  **AddItem** диалоговое окно.  Когда проект дочернего элемента отображает **AddItem** диалоговое окно родительский может реализовать  `IVsFilterAddProjectItemDlg` элементы интерфейса и фильтр, в противном случае были бы отображаются в проекте дочернего элемента.  
  
 При группировании функцией проектов под определенной родительскими проектами, можно реализовать `IVsFilterAddProjectItemDlg` когда пользователь выбирает  **добавьте элемент проекта** в контекстном меню во вложенных проекте.  Реализация `IvsFilterAddProjectItemDlg displays` элементы проекта или только файлы, относящиеся к этой группе.  Элементы проекта для других групп отфильтрованы из диалоговых окон, даже если они хранятся в том же каталоге.  
  
 При открытии пользователем **AddItem** диалоговое окно для дочернего элемента реализации родительского проекта  `IVsFilterAddProjectItemDlg` интерфейс вызывается.  
  
 `IVsFilterAddProjectItemDlg` может также реализовать интерфейс фильтрации по категориям.  Дополнительные сведения см. в разделах [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Вложенность проектов](../../extensibility/internals/nesting-projects.md)