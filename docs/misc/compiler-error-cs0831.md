---
title: "Ошибка компилятора CS0831 | Microsoft Docs"
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
  - "CS0831"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0831"
ms.assetid: f626a77d-3844-4438-954b-b8201e72b1b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0831
Дерево выражения не может иметь доступ к базовым членам.  
  
 Доступ к базовым членам означает выполнение вызова функции, который обычно является виртуальным вызовом функции в качестве невиртуального вызова функции в методе базового класса. Это не допускается в самом дереве выражения, но можно вызвать вспомогательный метод в классе, который вызывает метод базового класса.  
  
### Исправление ошибки  
  
1.  Если необходимо получить доступ к методу базового класса таким способом, создайте вспомогательный метод, который вызывает базовый класс, и в дереве выражений вызовите вспомогательный метод. Этот способ показан в следующем коде.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0831:  
  
```  
// cs0831.cs using System; using System.Linq; using System.Linq.Expressions; public class A { public virtual int BaseMethod() { return 1; } } public class C : A { public override int BaseMethod() { return 2; } public int Test(C c) { Expression<Func<int>> e = () => base.BaseMethod(); // CS0831 // Try the following line instead, // along with the BaseAccessHelper method. // Expression<Func<int>> e2 = () => BaseAccessHelper(); return 1; } // Uncomment to call from e2 expression above. // int BaseAccessHelper() // { //     return base.BaseMethod(); // } }   
```