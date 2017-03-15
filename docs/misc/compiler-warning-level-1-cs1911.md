---
title: "Предупреждение компилятора (уровень 1) CS1911 | Microsoft Docs"
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
  - "CS1911"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1911"
ms.assetid: 95e8a7a0-1c19-4930-a7e9-3ae4060e97d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS1911
Доступ к члену "имя" через ключевое слово "base" из анонимного метода, лямбда\-выражения, выражения запроса или итератора приводит к появлению непроверяемого кода. Рекомендуется переместить доступ во вспомогательный метод во вмещающем типе.  
  
 Вызов виртуальных функций с ключевым словом `base` в теле метода итератора или в анонимных методах приведет к непроверяемому коду. Непроверяемый код не сможет запуститься в среде с частичным доверием.  
  
 Один из способов устранения ошибки CS1911 состоит в том, чтобы переместить вызов виртуальной функции во вспомогательную функцию.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1911:  
  
```  
// CS1911.cs // compile with: /W:1 using System; delegate void D(); delegate D RetD(); class B { protected virtual void M() { Console.WriteLine("B.M"); } } class Der : B { protected override void M() { Console.WriteLine("D.M"); } void Test() { base.M(); } D Test2() { return new D(base.M); } public D CallBaseM() { return delegate () { base.M(); };   // CS1911 // try the following line instead // return delegate () { Test(); }; } public RetD DelToBaseM() { return delegate () { return new D(base.M); };   // CS1911 // try the following line instead // return delegate () { return Test2(); }; } } class Program { public static void Main() { Der der = new Der(); D d = der.CallBaseM(); d(); RetD rd = der.DelToBaseM(); rd()(); } }  
```