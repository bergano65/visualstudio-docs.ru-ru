---
title: "Параметр &quot;&lt;имя_параметра&gt;&quot; уже имеет соответствующий пропущенный аргумент | Microsoft Docs"
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
  - "vbc36566"
  - "bc36566"
helpviewer_keywords: 
  - "BC36566"
ms.assetid: b37af6bc-abd0-4436-bf8a-a467e3603342
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр &quot;&lt;имя_параметра&gt;&quot; уже имеет соответствующий пропущенный аргумент
Вызов процедуры предоставляет аргумент по имени после пропуска того же аргумента по позиции. Ниже представлен пример:  
  
```vb#  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... ' Argument Y is omitted by position, but supplied by name. Call ABC(6, , Y:=3)     
```  
  
 **Идентификатор ошибки:** BC36566  
  
### Исправление ошибки  
  
-   Предоставьте аргумент по позиции или удалите запятую, которая пропускает его.  
  
## См. также  
 [Передача аргументов по позиции и по имени](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)