---
title: "Ошибка компилятора CS1657 | Microsoft Docs"
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
  - "CS1657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1657"
ms.assetid: 6f0aeebe-5c90-4d5b-981c-1795d2e8fbb9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1657
Невозможно передать "параметр" как аргумент с ключевым словом ref или out, потому что "причина"  
  
 Эта ошибка происходит при передаче переменной как аргумента [ref](/dotnet/csharp/language-reference/keywords/ref) или [out](/dotnet/csharp/language-reference/keywords/out) в контексте, когда переменная доступна только для чтения. Контексты только для чтения включают переменные итерации [foreach](/dotnet/csharp/language-reference/keywords/foreach-in), переменные [using](/dotnet/csharp/language-reference/keywords/using-statement) и переменные `fixed`. Чтобы устранить эту ошибку, не вызывайте функции, принимающие переменную `foreach`, `using` или `fixed` в качестве параметра `ref` или `out` в блоках `using`, операторах `foreach` и `fixed`.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1657:  
  
```  
// CS1657.cs using System; class C : IDisposable { public int i; public void Dispose() {} } class CMain { static void f(ref C c) { } static void Main() { using (C c = new C()) { f(ref c);  // CS1657 } } }  
```  
  
## Пример  
 Следующий код иллюстрирует ту же проблему в операторе `fixed`:  
  
```  
// CS1657b.cs // compile with: /unsafe unsafe class C { static void F(ref int* p) { } static void Main() { int[] a = new int[5]; fixed(int* p = a) F(ref p); // CS1657 } }  
```