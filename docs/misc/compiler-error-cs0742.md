---
title: "Ошибка компилятора CS0742 | Microsoft Docs"
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
  - "CS0742"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0742"
ms.assetid: 078ee7af-17e4-4572-8fee-d97e09c9002b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0742
Тело запроса должно заканчиваться предложением select или предложением group.  
  
 Выражение запроса должно оканчиваться предложением `select` или `group` без какого\-либо продолжения.  
  
### Исправление ошибки  
  
1.  Добавьте в запрос [предложение select](/dotnet/csharp/language-reference/keywords/select-clause) или [предложение group](/dotnet/csharp/language-reference/keywords/group-clause).  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0742:  
  
```  
// cs0742.cs using System.Linq; public class Test { public static int Main() { int[] array = { 1, 2, 3 }; var query = from num in array; // CS0742 return 1; } }  
```  
  
 Если для сохранения результата группировки во временном идентификаторе в предложении `group` используется ключевое слово [into](/dotnet/csharp/language-reference/keywords/into), то оно не может быть последним предложением запроса. Предложение `select` или второе предложение `group` по\-прежнему требуется.  
  
## См. также  
 [Выражения запросов LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)