---
title: "Ошибка компилятора CS1666 | Microsoft Docs"
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
  - "CS1666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1666"
ms.assetid: 4d62aa9c-71b9-4c6e-8141-2426d20ac243
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1666
Нельзя использовать буферы фиксированного размера в нефиксированных выражениях. Попробуйте использовать оператор fixed.  
  
 Эта ошибка возникает при использовании буфера фиксированного размера в выражении, включающем класс, который не является фиксированным. Среда выполнения может свободно перемещать нефиксированный класс для оптимизации доступа к памяти, что может привести к ошибкам при использовании буфера фиксированного размера. Чтобы избежать этой ошибки, используйте в операторе ключевое слово `fixed`.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1666.  
  
```  
// CS1666.cs // compile with: /unsafe /target:library unsafe struct S { public fixed int buffer[1]; } unsafe class Test { S field = new S(); private bool example1() { return (field.buffer[0] == 0);   // CS1666 error } private bool example2() { // OK fixed (S* p = &field) { return (p->buffer[0] == 0); } } private bool example3() { S local = new S(); return (local.buffer[0] == 0); } }  
```