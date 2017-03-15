---
title: "Ошибка компилятора CS0412 | Microsoft Docs"
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
  - "CS0412"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0412"
ms.assetid: eeb2afbc-9416-4bcf-b116-d6adc5cfd4ca
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0412
"универсальный": имя параметра или локальной переменной не может совпадать с именем параметра типа метода  
  
 Существует конфликт имен между параметром типа универсального метода и локальной переменной в методе или один из параметров метода. Чтобы избежать этой ошибки, переименуйте все конфликтующие параметры и локальные переменные.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0412:  
  
```  
// CS0412.cs using System; class C { // Parameter name is the same as method type parameter name public void G<T>(int T)  // CS0412 { } public void F<T>() { // Method local variable name is the same as method type // parameter name double T = 0.0;  // CS0412 Console.WriteLine(T); } public static void Main() { } }  
```