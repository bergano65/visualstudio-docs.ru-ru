---
title: "Ошибка компилятора CS1660 | Microsoft Docs"
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
  - "CS1660"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1660"
ms.assetid: ae7fede3-471b-4e20-97a7-b80fdc2bb080
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1660
Невозможно преобразовать блок анонимного метода в тип "тип", поскольку он не является типом делегата  
  
 Эта ошибка возникает при попытке назначить блоку анонимного метода тип или преобразовать этот блок в тип, который не является типом делегата.  
  
 Следующий пример приводит к возникновению ошибки CS1660:  
  
```  
// CS1660.cs delegate int MyDelegate(); class C { static void Main() { int i = delegate { return 1; };  // CS1660 // Try this instead: // MyDelegate myDelegate = delegate { return 1; }; // int i = myDelegate(); } }  
```