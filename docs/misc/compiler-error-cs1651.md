---
title: "Ошибка компилятора CS1651 | Microsoft Docs"
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
  - "CS1651"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1651"
ms.assetid: ce1043e3-b453-4b4c-b949-f344834e3845
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1651
Поля доступного только для чтения статического поля "идентификатор" могут передаваться как параметры с ключевым словом ref или out только в статическом конструкторе  
  
 Эта ошибка возникает, если передать переменную в функцию, которая является членом статического поля только для чтения, в качестве аргумента ref. Так как параметры ref могут быть изменены функцией, это не допускается. Для устранения этой ошибки удалите ключевое слово **readonly** в поле или не передавайте члены поля readonly функции. Например, можно попытаться создать временную переменную, которая может быть изменена, и передать ее в качестве аргумента ref, как показано в приведенном ниже примере.  
  
 Следующий пример приводит к возникновению ошибки CS1651:  
  
```  
// CS1651.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { f(ref Outer.inner.i);  // CS1651 // Try this instead: // int tmp = Outer.inner.i; // f(ref tmp); } }  
```