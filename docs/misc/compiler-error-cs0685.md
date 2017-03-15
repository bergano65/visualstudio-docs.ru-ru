---
title: "Ошибка компилятора CS0685 | Microsoft Docs"
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
  - "CS0685"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0685"
ms.assetid: 20d7c6cf-a388-430f-b22b-232536912491
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0685
Член с атрибутом Conditional "член" не может иметь параметр out.  
  
 При использовании в методе атрибута <xref:System.Diagnostics.ConditionalAttribute> этот метод не может иметь параметр out. Это обусловлено тем, что значение переменной, используемой для параметра out, не может быть задано в случае, когда вызов метода компилируется в ничего. Чтобы избежать этой ошибки, удалите параметр out из объявления условного метода или не используйте атрибут Conditional.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0685.  
  
```  
// CS0685.cs using System.Diagnostics; class C { [Conditional("DEBUG")] void trace(out int i)  // CS0685 { i = 1; } }  
```