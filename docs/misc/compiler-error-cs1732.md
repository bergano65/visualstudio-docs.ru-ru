---
title: "Ошибка компилятора CS1732 | Microsoft Docs"
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
  - "CS1732"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1732"
ms.assetid: 72c7f7fc-d5f2-4538-9b02-50dda54d3b1e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1732
Требуется параметр.  
  
 Эта ошибка возникает, если лямбда\-выражение содержит запятую, следующую за входным параметром, однако следующий параметр не указывается.  
  
### Исправление ошибки  
  
1.  Либо удалите запятую, либо добавьте входной параметр, который компилятор ожидает найти после запятой.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1732:  
  
```  
// cs1732.cs // compile with: /target:library class Test { delegate void D(int x, int y); static void Main() { D d = (x,) => { }; // CS1732 } }  
```