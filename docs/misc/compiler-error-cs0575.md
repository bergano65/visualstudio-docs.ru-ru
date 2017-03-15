---
title: "Ошибка компилятора CS0575 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0575"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0575"
ms.assetid: e8f20960-94a6-41d0-807c-d49ad198ccf6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0575
Деструкторы могут содержаться только в типах классов.  
  
 Объект [struct](/dotnet/csharp/language-reference/keywords/struct) не может содержать деструктор.  
  
 В следующем примере возникает ошибка CS0575:  
  
```  
// CS0575.cs namespace x { public struct iii { ~iii()   // CS0575 { } public static void Main() { } } }  
```