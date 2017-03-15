---
title: "Предупреждение компилятора (уровень&#160;3) CS1717 | Microsoft Docs"
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
  - "CS1717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1717"
ms.assetid: 5b150a2c-5d61-4cd8-b4d4-e6c2b93b52c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;3) CS1717
Проведено присвоение той же переменной; действительно выполнить такое назначение, а не иное?  
  
 Это предупреждение возникает при назначении переменной самой себе, например `a = a`.  
  
 Это предупреждение создается в результате нескольких распространенных ошибок.  
  
-   Указание `a = a` в качестве условия инструкции **if**, например `if (a = a)`. Возможно, имелось в виду условие `if (a == a)`, которое всегда имеет значение true, так что это можно написать более сжато как `if (true)`.  
  
-   Опечатки. Возможно, имелось в виду `a = b`.  
  
-   В конструкторе, где параметр имеет то же имя, что и поле, не используется ключевое слово **this**: возможно, имелось в виду `this.a = a`.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1717.  
  
```  
// CS1717.cs // compile with: /W:3 public class Test { public static void Main() { int x = 0; x = x;   // CS1717 } }  
```