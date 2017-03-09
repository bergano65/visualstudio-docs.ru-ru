---
title: "Элемент &quot;&lt;имя_элемента&gt;&quot; не может быть объявлен как Partial, поскольку разделяемые методы должны быть Sub. | Microsoft Docs"
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
  - "vbc31437"
  - "bc31437"
helpviewer_keywords: 
  - "BC31437"
ms.assetid: 31ca12ab-2c26-4907-a253-e7c57bb4f34b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Элемент &quot;&lt;имя_элемента&gt;&quot; не может быть объявлен как Partial, поскольку разделяемые методы должны быть Sub.
Только процедуры `Sub` могут объявляться как разделяемые методы. Например, следующий код приводит к этой ошибке, поскольку `partialMethod` является функцией.  
  
```  
' Partial Private Function partialMethod(ByVal n As Integer) As Integer ' End Function  
```  
  
 **Идентификатор ошибки:** BC31437  
  
### Исправление ошибки  
  
-   Преобразуйте то, что вы объявляете как разделяемый метод, в `Sub`.  
  
-   В этом случае не следует использовать разделяемый метод.  
  
## См. также  
 [Разделяемые методы](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Подпрограммы](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)