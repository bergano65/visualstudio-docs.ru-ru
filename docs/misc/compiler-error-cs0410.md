---
title: "Ошибка компилятора CS0410 | Microsoft Docs"
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
  - "CS0410"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0410"
ms.assetid: a8b11042-9119-465e-abf6-235cbc7b8db5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0410
Ни одна из перегрузок "метод" не имеет допустимых типов возвращаемого значения и параметров  
  
 Эта ошибка возникает при попытке создать делегат с помощью функции, которая имеет неправильные типы параметров. Типы параметров делегата должны совпадать с типами параметров функции, которая присваивается делегату.  
  
## Пример  
 Следующий пример приводит к возникновению ошибок CS0410:  
  
```  
// CS0410.cs // compile with: /langversion:ISO-1 class Test { delegate void D(double d ); static void F(int i) { } static void Main() { D d = new D(F);  // CS0410 } }  
```