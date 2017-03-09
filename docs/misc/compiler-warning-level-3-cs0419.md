---
title: "Предупреждение компилятора (уровень&#160;3) CS0419 | Microsoft Docs"
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
  - "CS0419"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0419"
ms.assetid: de439ad5-422f-4ed6-96d6-69dade29c7b2
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;3) CS0419
Неоднозначная ссылка в атрибуте cref: "Имя метода 1".  Предполагается "Имя метода 2", но может также соответствовать другим перегрузкам, включая "Имя метода 3".  
  
 Не удалось разрешить ссылку в комментарии документации XML в коде. Это может происходить, если метод перегружен или если найдено два разных идентификатора с одинаковым именем. Чтобы разрешить предупреждение, используйте полное имя для устранения неоднозначности ссылки или заключите определенную перегрузку в скобки.  
  
 Следующий пример приводит к возникновению предупреждения CS0419:  
  
```  
// cs0419.cs // compile with: /doc:x.xml /W:3 interface I { /// text for F(void) void F(); /// text for F(int) void F(int i); } /// text for class MyClass public class MyClass { /// <see cref="I.F"/> public static void MyMethod(int i) { } /* Try this instead: /// <see cref="I.F(int)"/> public static void MyMethod(int i) { } */ /// text for Main public static void Main () { } }  
```