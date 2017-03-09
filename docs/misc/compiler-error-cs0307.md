---
title: "Ошибка компилятора CS0307 | Microsoft Docs"
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
  - "CS0307"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0307"
ms.assetid: 202a9985-ed7a-4e0a-9573-5624e066d314
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0307
"Конструкция" "идентификатор" не является универсальным методом. Для реализации списка выражений используйте круглые скобки вокруг выражения \<выражение\>.  
  
 Названная конструкция не является типом или методом, единственными конструкциями, которые могут принимать универсальные аргументы. Удалите аргументы типа в угловых скобках. Если необходим универсальный объект, объявите свою универсальную конструкцию как универсальный тип или метод.  
  
 В следующем примере возникает ошибка CS0307:  
  
```  
// CS0307.cs class C { public int P { get { return 1; } } public static void Main() { C c = new C(); int p = c.P<int>();  // CS0307 – C.P is a property // Try this instead // int p = c.P; } }  
```