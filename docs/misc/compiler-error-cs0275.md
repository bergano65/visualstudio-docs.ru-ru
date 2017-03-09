---
title: "Ошибка компилятора CS0275 | Microsoft Docs"
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
  - "CS0275"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0275"
ms.assetid: 4d59f11c-b0ea-4c91-b2cb-cbe3be9a9ba2
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0275
"метод доступа": модификаторы доступа не могут использоваться в методах доступа в интерфейсе  
  
 Эта ошибка возникает при использовании модификатора доступа в каком\-либо из методов доступа свойства или индексатора в интерфейсе. Для устранения этой ошибки удалите модификатор доступа.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0275:  
  
```  
// CS0275.cs public interface MyInterface { int Property { get; internal set;   // CS0275 } }  
```