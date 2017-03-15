---
title: "Ошибка компилятора CS0514 | Microsoft Docs"
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
  - "CS0514"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0514"
ms.assetid: 74ce3010-f9e9-458c-8b68-cfb908a3e7a2
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0514
"конструктор": статический конструктор не может иметь явный вызов конструктора с this или base  
  
 Не допускается вызывать `this` в статическом конструкторе, так как статический конструктор вызывается автоматически до создания любого экземпляра класса. Кроме того, статические конструкторы не наследуются и не могут вызываться непосредственно.  
  
 Дополнительные сведения см. в разделах [this](/dotnet/csharp/language-reference/keywords/this) и [базовые](/dotnet/csharp/language-reference/keywords/base).  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0514:  
  
```  
// CS0514.cs class A { static A() : base(0) // CS0514 { } public A(object o) { } } class B { static B() : this(null) // CS0514 { } public B(object o) { } }  
```