---
title: "Ошибка компилятора CS1649 | Microsoft Docs"
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
  - "CS1649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1649"
ms.assetid: 6355c7f2-157c-441d-8925-500062988636
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1649
Члены доступного только для чтения поля "идентификатор" могут передаваться как параметры с ключевым словом ref или out только в конструкторе  
  
 Эта ошибка возникает при передаче в функцию переменной, которая является членом поля `readonly`, в качестве аргумента `ref` или `out`. Так как параметры `ref` и `out` могут быть изменены функцией, такая передача не разрешается. Чтобы устранить эту ошибку, удалите ключевое слово `readonly` в поле или не передавайте члены поля `readonly` в функцию. Например, вы можете создать временную переменную, которая может быть изменена, и передать ее как аргумент `ref`, как показано в следующем примере.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1649:  
  
```  
// CS1649.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { Outer outer = new Outer(); f(ref outer.inner.i);  // CS1649 // Try this code instead: // int tmp = outer.inner.i; // f(ref tmp); } }  
```