---
title: "Расширение панели элементов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "средства [Visual Studio], панель элементов"
  - "панель элементов [Visual Studio SDK]"
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
caps.handback.revision: 38
manager: "douge"
---
# Расширение панели элементов
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Панель элементов** представляет коллекцию объектов, которые предоставляют функциональные возможности в редакторах и конструкторах через механизм перетаскивания IDE.  
  
 Существует два основных способа, которыми VSPackage работает с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **панелью элементов**.  
  
-   VSPackage может добавлять в **панель элементов** новые элементы данных и элементы управления.  
  
-   VSPackage может быть целевым объектом или потребителем существующих функциональных возможностей **панели элементов** с поддержкой операций перетаскивания и настройки внешнего вида **панели элементов**.  
  
## В этом подразделе  
 [Практическое руководство. Создание элемента управления панели элементов, использующего Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Описывается создание элемента управления "Панель элементов" с помощью шаблона элемента управления панели элементов Windows Forms.  
  
 [Создание элементов управления WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Описывается создание элемента управления "Панель элементов" с помощью шаблона элемента управления панели элементов WPF.  
  
 [Управление панелью элементов](/visual-cpp/misc/managing-the-toolbox)  
 Описывается, как VSPackage может управлять содержимым и внешним видом **панели элементов**.  
  
## Связанные подразделы  
 [Практическое руководство. Управление окном панели элементов](http://msdn.microsoft.com/ru-ru/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Описывается, как работать с **панелью элементов** в интегрированной среде разработки \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Практическое руководство. Управление панелью элементов](../Topic/How%20to:%20Control%20the%20Toolbox.md)  
 Описывается, как управлять **панелью элементов** с помощью модели программирования автоматизации.  
  
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Объясняется использование служб [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для создания элементов пользовательского интерфейса, соответствующих остальным частям [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].