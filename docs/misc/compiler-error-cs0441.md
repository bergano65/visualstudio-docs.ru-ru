---
title: "Ошибка компилятора CS0441 | Microsoft Docs"
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
  - "CS0441"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0441"
ms.assetid: 3f07500a-d479-424c-a0f4-c219be1b5a45
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0441
"класс": класс не может быть одновременно статическим и запечатанным  
  
 Эта ошибка возникает при объявлении класса, который является одновременно статическим и запечатанным. Статические классы изначально запечатаны, поэтому в модификаторе sealed нет необходимости. Для устранения этой ошибки используйте только один модификатор.  
  
 Следующий пример приводит к возникновению ошибки CS0441:  
  
```  
// CS0441.cs sealed static class MyClass { }   // CS0441  
```