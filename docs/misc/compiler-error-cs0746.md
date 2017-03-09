---
title: "Ошибка компилятора CS0746 | Microsoft Docs"
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
  - "CS0746"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0746"
ms.assetid: 36baf7f2-b092-422c-ab53-95154bfceb0a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0746
Недопустимый декларатор анонимного члена типа. Анонимные члены типа должны объявляться с помощью назначения члена, простого имени или доступа члена.  
  
 Анонимный тип должен объявляться с помощью назначения члена, простого имени или доступа к члену.  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что в объявлении используются только назначения члена, простые имена и выражения доступа к члену.  
  
## Пример  
 Приведенный ниже код приводит к возникновению ошибки CS0746 в объявлении `incorrect_1` и `incorrect_2`. В следующих объявлениях показаны два правильных способа объявления анонимного типа:  
  
```  
// cs0746.cs public class C { public static int Main() { int i = 100; string s = "Bottles of beer."; var incorrect_1 = new { a.b = 1 }; // CS0746 var incorrect_2 = new {100, "Bottles of beer."}; // CS0746 var correct_1 = new { i, s }; //OK var correct_2 = new {num = i, message = s}; // OK return 1; } }  
  
```  
  
## См. также  
 [Анонимные типы](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)