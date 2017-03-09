---
title: "Предупреждение компилятора (уровень&#160;1) CS0672 | Microsoft Docs"
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
  - "CS0672"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0672"
ms.assetid: 140a8708-97d0-444b-980b-62e74328cafb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS0672
Член "член1" переопределяет устаревший член "член2". Добавьте к "член1" атрибут Obsolete.  
  
 Компилятор обнаружил ключевое слово `override`, примененное к методу, помеченному атрибутом `obsolete`. Однако переопределяющий метод не помечен как устаревший. В случае вызова переопределяющий метод будет продолжать вызывать ошибку [CS0612](/dotnet/csharp/misc/cs0612).  
  
 Проверьте объявления методов и явным образом укажите, должен ли метод \(и все его переопределения\) помечаться как `obsolete`.  
  
 Следующий пример приводит к возникновению предупреждения CS0672:  
  
```  
// CS0672.cs // compile with: /W:1 class MyClass { [System.Obsolete] public virtual void ObsoleteMethod() { } } class MyClass2 : MyClass { public override void ObsoleteMethod()   // CS0672 { } } class MainClass { static public void Main() { } }  
```