---
title: "Ошибка компилятора CS1663 | Microsoft Docs"
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
  - "CS1663"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1663"
ms.assetid: 013f36ac-8925-4cee-9008-54fa7ad1324b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1663
Тип буфера фиксированного размера должен входить в следующий список: bool, byte, short, int, long, char, sbyte, ushort, uint, ulong, float или double.  
  
 Буфер фиксированного размера не могут быть любого типа, отличного от перечисленных. Чтобы избежать этой ошибки, используйте другой тип или не используйте массив фиксированной длины.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1663:  
  
```  
// CS1663.cs // compile with: /unsafe /target:library unsafe struct C { fixed string ab[10];   // CS1663 }  
```