---
title: "&quot;&lt;имя_метода&gt;&quot; не может переопределять метод, который был переобъявлен | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31406"
  - "bc31406"
helpviewer_keywords: 
  - "BC31406"
ms.assetid: 08ed11a6-3399-49fa-ac6e-c5df1328a24e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_метода&gt;&quot; не может переопределять метод, который был переобъявлен
Предпринята попытка переопределения метода, затемняющего другой член.  
  
 **Идентификатор ошибки:** BC31406  
  
### Исправление ошибки  
  
-   Используйте модификатор `Shadows` для переопределения затемненных членов.  
  
## См. также  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)