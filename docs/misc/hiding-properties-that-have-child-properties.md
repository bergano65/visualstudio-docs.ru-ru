---
title: "Скрытие свойств, имеющих дочерние свойства | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "свойства [Visual Studio SDK], скрытие"
  - "окно свойств, скрытие свойств, имеющие дочерние свойства"
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Скрытие свойств, имеющих дочерние свойства
Вы хотели бы скрывать свойства, имеющие свойства дочерних элементов:  
  
-   Если вложенные проекты, где родительский проект программным образом управлять некоторые аспекты проекта дочернего элемента.  
  
-   При использовании элемента управления, используя специальное конструктором, а не нужно предоставить разработчикам полный доступ ко всем свойствам элемента управления.  
  
-   Если владение области объекта и требуется ограничить представление свойств.  
  
### Скрывать свойства, имеющие свойства дочерних элементов  
  
1.  Установка `pfDisplay` параметр in  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> В  `FALSE`.  
  
2.  Установка `pfHide` параметр in  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> В  `TRUE`.  
  
## См. также  
 [Отображение сетки свойств](../extensibility/internals/properties-display-grid.md)