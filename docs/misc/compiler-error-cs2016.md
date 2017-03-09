---
title: "Ошибка компилятора CS2016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2016"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2016"
ms.assetid: 69f77502-f726-4856-ac87-e556eeb67349
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS2016
Кодовая страница "кодовая\_страница" является недопустимой или не установлена  
  
 Параметру компилятора [\/codepage](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option) передано недопустимое значение.  
  
 При компиляции следующего примера возникнет ошибка CS2016:  
  
```  
// CS2016.cs // compile with: /codepage:x // CS2016 expected class MyClass { public static void Main() { } }  
```