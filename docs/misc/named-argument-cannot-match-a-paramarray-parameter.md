---
title: "Именованный аргумент не должен соответствовать параметру ParamArray. | Microsoft Docs"
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
  - "bc30587"
  - "vbc30587"
helpviewer_keywords: 
  - "BC30587"
ms.assetid: aff179af-96f2-4157-971e-881d8e08f5f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Именованный аргумент не должен соответствовать параметру ParamArray.
Предоставлен именованный аргумент \(указанный в виде объявленного имени аргумента, за которым следует двоеточие, знак равенства и значение аргумента\); однако невозможно передать массив параметров по имени. При вызове процедуры указано неопределенное число разделенных запятыми аргументов для массива параметров, а компилятор не может связывать несколько аргументов с одним именем.  
  
 **Идентификатор ошибки:** BC30587  
  
### Исправление ошибки  
  
-   Передайте аргумент по позиции, а не по имени.  
  
## См. также  
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Передача аргументов по позиции и по имени](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)