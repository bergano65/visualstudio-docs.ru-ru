---
title: "Реализация команды обработки вложенных проектов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "вложенные проекты, реализация обработка команд"
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Реализация команды обработки вложенных проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Интегрированная среда разработки может передавать команды, которые передаются посредством <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> и  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейсы к вложенным проекты или родительским проекты могут фильтровать или переопределить команды.  
  
> [!NOTE]
>  Только команды обычно обрабатывается родительским проектом могут быть отфильтрованы.  Команды как **Build** и  **Deploy** в качестве интегрированной средой разработки не могут быть отфильтрованы.  
  
 Следующие шаги описывают процесс для реализации обработки команд.  
  
## Процедуры  
  
#### К обработке команды "  
  
1.  Когда пользователь выбирает вложенную проект или узел во вложенных проекте.  
  
    1.  Интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод.  
  
     — либо —  
  
    1.  Если команда была создана в окне иерархия, как команда контекстного меню в обозревателе решений в интегрированной среде разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> метод родительские проекта.  
  
2.  Родительский проект может просмотреть параметры, передаваемые `QueryStatus`как  `pguidCmdGroup` и  `prgCmds`, для указания, должен ли родительский проект фильтрации команды.  Если реализуется родительский проект фильтрации команды, он должен задать:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     Затем родительский проект должен возвращать `S_OK`.  
  
     Если родительский проект не фильтрует команда, он должен просто возвратить `S_OK`.  В этом случае среда разработки автоматически направляет команду к проекту дочернего элемента.  
  
     Родительский проект не должен направлять команду к проекту дочернего элемента.  Интегрированная среда разработки выполняет эту задачу.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Команды, меню и панелей инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Вложенность проектов](../../extensibility/internals/nesting-projects.md)