---
title: "Ошибка компилятора CS1689 | Microsoft Docs"
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
  - "CS1689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1689"
ms.assetid: 5fa6e845-40ef-4451-81ee-acbe2665527a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1689
Атрибут "Имя Атрибута" допустим только в методах или в классах атрибутов.  
  
 Эта ошибка возникает только с атрибутом **ConditionalAttribute**. Как говорится в сообщении, этот атрибут может использоваться только в методах или в классах атрибутов. Например, при попытке применения этого атрибута к классу возникнет данная ошибка.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1689.  
  
```  
// CS1689.cs // compile with: /target:library [System.Diagnostics.Conditional("A")]   // CS1689 class MyClass {}  
```