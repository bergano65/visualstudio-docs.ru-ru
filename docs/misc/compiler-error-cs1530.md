---
title: "Ошибка компилятора CS1530 | Microsoft Docs"
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
  - "CS1530"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1530"
ms.assetid: 3844b5ef-e0ec-42df-9267-72689020f128
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1530
Ключевое слово "new" не может использоваться для элементов, определенных в пространстве имен  
  
 Нет необходимости указывать ключевое слово [new](/dotnet/csharp/language-reference/keywords/new) для любой конструкции внутри [пространства имен](/dotnet/csharp/language-reference/keywords/namespace).  
  
 Следующий пример приводит к возникновению ошибки CS1530:  
  
```  
// CS1530.cs namespace a { new class i   // CS1530 { } // try the following instead class ii { public static void Main() { } } }  
```