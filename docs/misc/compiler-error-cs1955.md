---
title: "Ошибка компилятора CS1955 | Microsoft Docs"
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
  - "CS1955"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1955"
ms.assetid: 38a8542d-da53-4739-b807-46c8c077363c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1955
Невызываемый член "имя" не может использоваться как метод.  
  
 Вызывать можно только методы и делегаты. Эта ошибка возникает при попытке использования пустых скобок для вызова любых элементов, кроме методов и делегатов.  
  
### Исправление ошибки  
  
1.  Удалите скобки из выражения.  
  
## Пример  
 В приведенном ниже примере кода возникает ошибка CS1955, так как происходит попытка вызвать поле и свойство с помощью оператора вызова метода [\(\)](/dotnet/csharp/language-reference/operators/invocation-operator). Поле или свойство вызвать невозможно, но можно обратиться к хранящемуся в нем значению с помощью оператора доступа к члену \([.](/dotnet/csharp/language-reference/operators/member-access-operator)\).  
  
```  
// cs1955.cs class A { public int x = 0; public int X { get { return x; } set { x = value; } } } class Test { static int Main() { A a = new A(); a.x(); // CS1955 a.X(); // CS1955 // Try this line instead: // int num = a.x; } }  
```