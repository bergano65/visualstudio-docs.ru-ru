---
title: "Ошибка компилятора CS0144 | Microsoft Docs"
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
  - "CS0144"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0144"
ms.assetid: 3904cab1-05bd-44ec-81d0-e36c5656f742
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0144
Не удается создать экземпляр абстрактного класса или интерфейса "интерфейс"  
  
 Нельзя создать экземпляр [абстрактного](/dotnet/csharp/language-reference/keywords/abstract) класса или [интерфейса](/dotnet/csharp/language-reference/keywords/interface). Дополнительные сведения см. в разделе [Интерфейсы](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Следующий пример приводит к возникновению ошибки CS0144:  
  
```  
// CS0144.cs interface MyInterface { } public class MyClass { public static void Main() { MyInterface myInterface = new MyInterface ();   // CS0144 } }  
```