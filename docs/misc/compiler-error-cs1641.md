---
title: "Ошибка компилятора CS1641 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1641"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1641"
ms.assetid: ba6eab47-c28b-4531-b6a0-6d538b236d19
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1641
Поле буфера фиксированного размера должно иметь спецификатор размера массива после имени поля.  
  
 В отличие от обычных массивов буферам фиксированного размера требуется указание размера константы в момент объявления. Чтобы устранить эту ошибку, добавьте положительный целочисленный литерал или постоянное положительное целое число и поместите квадратные скобки после идентификатора.  
  
 Следующий пример приводит к возникновению ошибки CS1641:  
  
```  
// CS1641.cs // compile with: /unsafe /target:library unsafe struct S { fixed int [] a;  // CS1641 // OK fixed int b [10]; const int c = 10; fixed int d [c]; }  
```