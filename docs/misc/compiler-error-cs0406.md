---
title: "Ошибка компилятора CS0406 | Microsoft Docs"
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
  - "CS0406"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0406"
ms.assetid: 9d69681c-e261-4e5e-9361-ea566de12f2e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0406
Ограничение типа класса "ограничение" должно идти перед любыми другими ограничениями  
  
 Если для универсального типа или метода задано ограничение типа класса, это ограничение должно быть указано в списке первым. Чтобы избежать этой ошибки, переместите ограничение типа класса в начало списка ограничений.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0406:  
  
```  
// CS0406.cs // compile with: /target:library interface I {} class C {} class D<T> where T : I, C {}   // CS0406 class D2<T> where T : C, I {}   // OK  
```