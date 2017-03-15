---
title: "Ошибка компилятора CS0153 | Microsoft Docs"
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
  - "CS0153"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0153"
ms.assetid: 3a0791e9-0ab9-4eaa-a230-d39aabaa9d5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0153
Оператор goto case допустим только внутри оператора выбора.  
  
 Предпринята попытка использовать синтаксис [выбора](/dotnet/csharp/language-reference/keywords/switch) за пределами оператора **выбора**. Дополнительные сведения см. в разделе [switch](/dotnet/csharp/language-reference/keywords/switch).  
  
 Следующий пример приводит к возникновению ошибки CS0153:  
  
```  
// CS0153.cs public class a { public static void Main() { goto case 5;   // CS0153 } }  
```