---
title: "Классы &quot;NotInheritable&quot; не могут содержать членов, объявленных как &quot;&lt;имя_описателя&gt;&quot;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30607"
  - "bc30607"
helpviewer_keywords: 
  - "BC30607"
ms.assetid: c800e24e-d055-402f-b378-6d2f4041ff16
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Классы &quot;NotInheritable&quot; не могут содержать членов, объявленных как &quot;&lt;имя_описателя&gt;&quot;.
Модификаторы переопределения нельзя использовать с классами `NotInheritable`, так как их члены не могут быть переопределены.  
  
 **Идентификатор ошибки:** BC30607  
  
### Исправление ошибки  
  
-   Удалите модификаторы переопределения, такие как `Overridable`, `NotOverridable` или `MustOverride`, из определения класса.  
  
## См. также  
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)