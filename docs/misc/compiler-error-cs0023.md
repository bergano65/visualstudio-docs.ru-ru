---
title: "Ошибка компилятора CS0023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0023"
ms.assetid: 7a30073c-99de-41fa-ac6d-4a0dfbb76de9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0023
Оператор "оператор" не может применяться к операнду типа "тип"  
  
 Предпринята попытка применить оператор к переменной, тип которой не предназначен для работы с этим оператором. Дополнительные сведения см. в разделах [Типы](/dotnet/csharp/programming-guide/types/index) и [Операторы C\#](/dotnet/csharp/language-reference/operators/index).  
  
 При компиляции следующего примера возникнет ошибка CS0023:  
  
```  
// CS0023.cs namespace x { public class a { public static void Main() { string s = "hello"; s = -s;   // CS0023, minus operator not allowed on strings } } }  
```