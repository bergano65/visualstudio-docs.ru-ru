---
title: "Ошибка компилятора CS0644 | Microsoft Docs"
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
  - "CS0644"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0644"
ms.assetid: 835f3ee2-f897-4ba2-ad13-af629a9ab7fe
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0644
"класс1" не может наследовать от специального класса "класс2"  
  
 Классы не могут явно наследоваться от любых из следующих базовых классов:  
  
-   **System.Enum**  
  
-   **System.ValueType**  
  
-   **System.Delegate**  
  
-   **System.Array**  
  
 Они используются компилятором как неявные базовые классы. Например, **System.ValueType** является неявным базовым классом структур.  
  
 Следующий пример приводит к возникновению ошибки CS0644:  
  
```  
// CS0644.cs class MyClass : System.ValueType   // CS0644 { }  
```