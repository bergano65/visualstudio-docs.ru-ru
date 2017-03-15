---
title: "Предупреждение компилятора (уровень&#160;2) CS0464 | Microsoft Docs"
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
  - "CS0464"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0464"
ms.assetid: 3dff97d4-e1f6-4a71-91e2-68cffc38d49a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;2) CS0464
Результатом сравнения с пустым значением типа "тип" всегда является "false"  
  
 Это предупреждение появляется при выполнении сравнения обнуляемой переменной со значением null, когда используется сравнение, отличное от `==` или `!=`. Чтобы устранить эту ошибку, проверьте, действительно ли нужно проверять значение на `null`. Сравнение типа `i == null` может давать результат true или false. Сравнение типа `i > null` всегда дает false.  
  
## Пример  
 Следующий пример приводит к возникновению предупреждения CS0464:  
  
```  
// CS0464.cs class MyClass { public static void Main() { int? i = 0; if (i < null) ;   // CS0464 i++; } }  
```