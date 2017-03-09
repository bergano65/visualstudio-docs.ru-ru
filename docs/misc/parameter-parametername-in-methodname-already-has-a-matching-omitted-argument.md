---
title: "Параметр &quot;&lt;имя_параметра&gt;&quot; в методе &quot;&lt;имя_метода&gt;&quot; уже имеет соответствующий пропущенный аргумент | Microsoft Docs"
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
  - "vbc32021"
  - "bc32021"
helpviewer_keywords: 
  - "BC32021"
ms.assetid: f51d29ba-c5b3-4731-a426-4c5ba11b4e1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр &quot;&lt;имя_параметра&gt;&quot; в методе &quot;&lt;имя_метода&gt;&quot; уже имеет соответствующий пропущенный аргумент
Вызов процедуры предоставляет аргумент по имени после пропуска того же аргумента по позиции, например:  
  
```  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... Call ABC(6, , Y:=3)   ' Argument Y omitted by position, supplied by name.  
```  
  
 **Идентификатор ошибки:** BC32021  
  
### Исправление ошибки  
  
-   Предоставьте аргумент по позиции или удалите запятую, которая пропускает его.  
  
## См. также  
 [Передача аргументов по позиции и по имени](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)