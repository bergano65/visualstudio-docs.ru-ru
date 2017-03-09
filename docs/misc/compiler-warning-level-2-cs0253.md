---
title: "Предупреждение компилятора (уровень&#160;2) CS0253 | Microsoft Docs"
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
  - "CS0253"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0253"
ms.assetid: e02d5dac-c2d9-45ca-9dd3-dda06c96f4d6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;2) CS0253
Возможно, непреднамеренное сравнение ссылок; для получения сравнения значений приведите правую часть к типу "тип"  
  
 Компилятор выполняет сравнение ссылок. Если нужно сравнить значения строк, приведите правую часть выражения к `type`.  
  
 Следующий пример приводит к возникновению предупреждения CS0253:  
  
```  
// CS0253.cs // compile with: /W:2 using System; class MyClass { public static void Main() { string s = "11"; object o = s + s; bool c = s == o;   // CS0253 // try the following line instead // bool c = s == (string)o; } }  
```