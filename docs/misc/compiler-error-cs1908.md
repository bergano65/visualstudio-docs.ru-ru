---
title: "Ошибка компилятора CS1908 | Microsoft Docs"
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
  - "CS1908"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1908"
ms.assetid: d7da31c2-48ef-4401-b885-3459b4d7f6f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1908
Тип аргумента для атрибута DefaultValue должен соответствовать типу параметра  
  
 Это ошибка возникает при использовании неверного аргумента для значения атрибута <xref:System.ComponentModel.DefaultValueAttribute>. Используйте значение, соответствующее типу параметра.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS1908:  
  
```  
// CS1908.cs // compile with: /target:library using System.Runtime.InteropServices; public interface ISomeInterface { void Bad([Optional] [DefaultParameterValue("true")] bool b);   // CS1908 void Good([Optional] [DefaultParameterValue(true)] bool b);   // OK }  
```