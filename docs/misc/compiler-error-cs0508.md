---
title: "Ошибка компилятора CS0508 | Microsoft Docs"
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
  - "CS0508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0508"
ms.assetid: 28403573-6e64-4496-918d-fb50c8851e51
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0508
"Тип 1": типом возврата должен быть "Тип 2", чтобы соответствовать переопределенному члену "Имя\_члена".  
  
 Предпринята попытка изменить тип возврата в переопределении метода. Чтобы устранить эту ошибку, убедитесь, что оба метода объявляют один и тот же тип возврата.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0508.  
  
```  
// CS0508.cs // compile with: /target:library abstract public class Clx { public int i = 0; // Return type is int. abstract public int F(); } public class Cly : Clx { public override double F() { return 0.0;   // CS0508 } }  
```