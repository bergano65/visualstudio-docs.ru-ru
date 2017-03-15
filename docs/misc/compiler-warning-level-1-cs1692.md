---
title: "Предупреждение компилятора (уровень 1) CS1692 | Microsoft Docs"
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
  - "CS1692"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1692"
ms.assetid: 1a6d52e1-0ebb-4990-ac0b-36b05a884a19
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS1692
Недопустимое число  
  
 Много директив препроцессора, таких как `#pragma` и `#line`, используют числа в качестве параметров. Одно из этих чисел является недопустимым, так как оно слишком велико, имеет неправильный формат, содержит недопустимые знаки и т. п. Чтобы исправить эту ошибку, исправьте число.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1692.  
  
```  
// CS1692.cs #pragma warning disable a  // CS1692 // Try this instad: // #pragma warning disable 1691 class A { static void Main() { } }  
```