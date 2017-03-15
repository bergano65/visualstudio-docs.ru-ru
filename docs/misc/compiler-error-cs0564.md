---
title: "Ошибка компилятора CS0564 | Microsoft Docs"
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
  - "CS0564"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0564"
ms.assetid: 4c152e10-eb22-4437-a85f-1599c76470e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0564
Тип первого операнда переопределенного оператора сдвига должен совпадать с вмещающим типом, а тип второго операнда должен быть int.  
  
 Предпринята попытка перегрузить оператор сдвига \(\<\< или \>\>\) с неверно типизированными операндами. Первый операнд должен быть типом, а второй операнд должен иметь тип `int`.  
  
 В следующем примере возникает ошибка CS0564:  
  
```  
// CS0564.cs using System; class C { public static int operator << (C c1, C c2) // CS0564 // To correct, change second operand to int, like so: // public static int operator << (C c1, int c2) { return 0; } static void Main() { } }  
```