---
title: "Ошибка компилятора CS0841 | Microsoft Docs"
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
  - "CS0841"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0841"
ms.assetid: eb67c244-a930-4291-ae2a-5832e8916ed7
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0841
Невозможно использовать локальную переменную "имя" до ее объявления.  
  
 Переменная должна быть объявлена, прежде чем можно будет ее использовать.  
  
### Исправление ошибки  
  
1.  Переместите объявление переменной перед строкой, где возникает ошибка.  
  
## Пример  
 В следующем примере возникает ошибка CS0841:  
  
```  
// cs0841.cs using System; public class C { public static int Main() { j = 5; // CS0841 int j; // To fix, move this line up. return 1; } }  
```