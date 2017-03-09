---
title: "Ошибка компилятора CS1545 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1545"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1545"
ms.assetid: 56c377b5-4cf1-4c7d-b51d-463bad78f3ef
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1545
Свойство, индексатор или событие "свойство" не поддерживается в данном языке; попробуйте напрямую вызвать метод доступа set или get.  
  
 Код использует объект, имеющий [индексатор](/dotnet/csharp/programming-guide/indexers/index), не являющийся индексатором по умолчанию, и пытается использовать индексированный синтаксис. Чтобы устранить эту ошибку, вызовите метод доступа `get` или `set` свойства.  
  
## Пример  
  
```  
// CPP1545.cpp // compile with: /clr /LD // a Visual C++ program using namespace System; public ref struct Employee { Employee( String^ s, int d ) {} property String^ name { String^ get() { return nullptr; } } }; public ref struct Manager { property Employee^ Report [String^] { Employee^ get(String^ s) { return nullptr; } void set(String^ s, Employee^ e) {} } };  
```  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1545.  
  
```  
// CS1545.cs // compile with: /r:CPP1545.dll class x { public static void Main() { Manager Ed = new Manager(); Employee Bob = new Employee("Bob Smith", 12); Ed.Report[ Bob.name ] = Bob;   // CS1545 Ed.set_Report( Bob.name, Bob);   // OK } }  
```