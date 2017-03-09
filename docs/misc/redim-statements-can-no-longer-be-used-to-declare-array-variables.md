---
title: "Операторы &quot;ReDim&quot; больше не могут использоваться при объявлении переменных для массивов. | Microsoft Docs"
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
  - "bc30811"
  - "vbc30811"
helpviewer_keywords: 
  - "BC30811"
ms.assetid: 9227a06e-a997-4b16-9977-19e2bce9035b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы &quot;ReDim&quot; больше не могут использоваться при объявлении переменных для массивов.
`ReDim` может использоваться только для изменения размера существующего массива.  
  
 **Идентификатор ошибки:** BC30811  
  
### Исправление ошибки  
  
-   Укажите размер массивов при их объявлении; например:  
  
    ```  
    Dim X(20) As Integer  
    ```  
  
## См. также  
 [Сводка по массивам](/dotnet/visual-basic/language-reference/keywords/arrays-summary)   
 [Оператор ReDim](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [ReDim Statement Changes in Visual Basic](http://msdn.microsoft.com/ru-ru/b4da14db-ff23-490f-b3c6-d7ae1b649532)