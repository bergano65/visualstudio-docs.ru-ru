---
title: "Ошибка компилятора CS1715 | Microsoft Docs"
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
  - "CS1715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1715"
ms.assetid: 740044d1-a61c-4156-bc6a-adf26c7499ec
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1715
"Тип1": тип должен быть "Тип2", чтобы соответствовать переопределенному члену "Имя\_члена"  
  
 Эта ошибка аналогична ошибке, описанной в разделе [Ошибка компилятора CS0508](../misc/compiler-error-cs0508.md), за тем исключением, что ошибка CS0508 теперь применяется к методам, имеющим типы возвращаемых данных, тогда как ошибка CS1715 применяется к свойствам и индексаторам, которые имеют не "типы возвращаемых данных", а просто "типы".  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS1715:  
  
```  
// CS1715.cs abstract public class Base { abstract public int myProperty { get; set; } } public class Derived : Base { int myField; public override double myProperty  // CS1715 // try the following line instead // public override int myProperty { get { return myField; } set { myField;= value; } } public static void Main() { Derived d = new Derived(); d.myProperty = 5; } }  
```