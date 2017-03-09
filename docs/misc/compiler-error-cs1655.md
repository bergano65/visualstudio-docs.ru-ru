---
title: "Ошибка компилятора CS1655 | Microsoft Docs"
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
  - "CS1655"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1655"
ms.assetid: 041e9daa-c026-494f-b086-0db9a23c969b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1655
Невозможно передать поля "переменная" как аргумент с ключевым словом ref или out, потому что это "тип\_переменной\_только\_для\_чтения"  
  
 Эта ошибка происходит при попытке передать в функцию в качестве аргумента ref или out член переменной [foreach](/dotnet/csharp/language-reference/keywords/foreach-in), [using](/dotnet/csharp/language-reference/keywords/using-statement) или [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement). Так как в данных контекстах эти переменные доступны только для чтения, такая передача не разрешается.  
  
 При компиляции следующего примера возникнет ошибка CS1655:  
  
```  
// CS1655.cs struct S { public int i; } class CMain { static void f(ref int iref) { } public static void Main() { S[] sa = new S[10]; foreach(S s in sa) { CMain.f(ref s.i);  // CS1655 } } }  
```