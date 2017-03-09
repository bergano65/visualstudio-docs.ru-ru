---
title: "Ошибка компилятора CS0758 | Microsoft Docs"
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
  - "CS0758"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0758"
ms.assetid: 06ddd548-1311-40db-9078-8a18107b8346
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0758
Параметр params должен использоваться в обоих объявлениях разделяемого метода или не должен использоваться ни в одном из них.  
  
 Если в одной части разделяемого метода указан параметр `params`, то он должен быть указан и в другой части.  
  
### Исправление ошибки  
  
1.  Либо добавьте модификатор `params` в одной части метода, либо удалите его из другой.  
  
## Пример  
 При компиляции следующего кода возникнет ошибка CS0758:  
  
```  
using System; public partial class C { partial void Part(int i, params char[] array); partial void Part(int i, char[] array) // CS0758 { } public static int Main() { return 1; } }  
```  
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)