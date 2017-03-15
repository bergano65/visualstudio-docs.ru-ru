---
title: "Ошибка компилятора CS0425 | Microsoft Docs"
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
  - "CS0425"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0425"
ms.assetid: cec0391c-a641-43bc-8557-92b23f6ca685
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0425
Ограничения для параметра типа "параметр типа" метода "метод" должны соответствовать ограничениям для параметра типа "параметр типа" интерфейсного метода "метод". Попробуйте использовать явную реализацию интерфейса.  
  
 Эта ошибка возникает, если виртуальный универсальный метод переопределяется в производном классе и ограничения метода в производном классе не совпадают с ограничениями метода в базовом классе. Чтобы избежать этой ошибки, убедитесь в том, что предложения `where` в обоих объявлениях идентичны, или реализуйте интерфейс явным образом.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0425:  
  
```  
// CS0425.cs class C1 { } class C2 { } interface IBase { void F<ItemType>(ItemType item) where ItemType : C1; } class Derived : IBase { public void F<ItemType>(ItemType item) where ItemType : C2  // CS0425 { } } class CMain { public static void Main() { } }  
```  
  
## Пример  
 Ограничения могут совпадать не буквально, так как набор ограничений имеет то же значение. Например, следующий код верен:  
  
```  
// CS0425b.cs interface J<Z> { } interface I<S> { void F<T>(S s, T t) where T: J<S>, J<int>; } class C : I<int> { public void F<X>(int s, X x) where X : J<int> { } public static void Main() { } }  
```