---
title: "Ошибка компилятора CS0202 | Microsoft Docs"
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
  - "CS0202"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0202"
ms.assetid: 7088850f-c206-4b95-9586-a0fa3d876c0c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0202
Оператор foreach требует, чтобы возвращаемый тип "тип" в "type.GetEnumerator\(\)" имел соответствующий открытый метод MoveNext и открытое свойство Current  
  
 Функция <xref:System.Collections.IEnumerable.GetEnumerator%2A>, используемая для включения поддержки операторов foreach, не может возвращать указатель или массив; она должна возвращать экземпляр класса, который может функционировать как перечислитель. Чтобы функция могла использоваться как перечислитель, она должна включать открытое свойство Current и открытый метод MoveNext.  
  
> [!NOTE]
>  В C\# 2.0 компилятор автоматически создает свойство Current и метод MoveNext. Дополнительные сведения см. в примере кода в разделе [Универсальные интерфейсы](/dotnet/csharp/programming-guide/generics/generic-interfaces).  
  
 Следующий пример приводит к возникновению ошибки CS0202:  
  
```  
// CS0202.cs public class C1 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public static implicit operator C1 (int c1) { return 0; } } public class C2 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public C1[] GetEnumerator () // try the following line instead // public C1 GetEnumerator () { return null; } } public class MainClass { public static void Main () { C2 c2 = new C2(); foreach (C1 x in c2)   // CS0202 { System.Console.WriteLine(x.Current); } } }  
```