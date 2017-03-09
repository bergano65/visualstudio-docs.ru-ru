---
title: "Ошибка компилятора CS0762 | Microsoft Docs"
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
  - "CS0762"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0762"
ms.assetid: 7cedd1af-ffe6-4ca7-82fb-faa9e98014a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0762
Невозможно создать делегат на основе метода "метод", так как он является разделяемым методом без реализующего объявления  
  
 Разделяемый метод может не иметь реализующего объявления. Однако делегат требует, чтобы метод, который он инкапсулирует, имел реализацию.  
  
### Исправление ошибки  
  
1.  Предоставьте реализацию метода, используемого для инициализации делегата.  
  
## Пример  
  
```  
public delegate void TestDel(); public partial class C { partial void Part(); public static int Main() { C c = new C(); TestDel td = new TestDel(c.Part); // CS0762 return 1; } }  
```