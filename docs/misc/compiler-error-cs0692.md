---
title: "Ошибка компилятора CS0692 | Microsoft Docs"
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
  - "CS0692"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0692"
ms.assetid: d2fd650b-1f84-44b1-8c7e-471cad92a85e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0692
Повторяющийся параметр типа "идентификатор"  
  
 Одно и то же имя нельзя использовать несколько раз в списке параметров типа. Удалите или переименуйте повторяющиеся параметры типа.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0692:  
  
```  
// CS0692.cs // compile with: /target:library class C <T, A, T>   // CS0692 { } class D <T, T>   // CS0692 { }  
```