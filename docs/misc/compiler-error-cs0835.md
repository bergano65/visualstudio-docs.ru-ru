---
title: "Ошибка компилятора CS0835 | Microsoft Docs"
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
  - "CS0835"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0835"
ms.assetid: 593c26f6-6d82-49a6-8ace-4d29dd9f5fbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0835
Невозможно преобразовать лямбда\-выражение в дерево выражения, чей аргумент типа "тип" не является типом делегата.  
  
 Если лямбда\-выражение преобразуется в дерево выражения, это дерево выражения должно иметь тип делегата для своего аргумента. Кроме того, лямбда\-выражение должно быть преобразуемым в тип делегата.  
  
### Исправление ошибки  
  
1.  Измените параметр типа с `int` на тип делегата, например `Func<int,int>`.  
  
## Пример  
 В следующем примере возникает ошибка CS0835:  
  
```  
// cs0835.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<int> e = x => x + 1; // CS0835 // Try the following line instead. // Expression<Func<int,int>> e2 = x => x + 1; return 1; } }  
```