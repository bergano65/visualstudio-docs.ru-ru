---
title: "Ошибка компилятора CS1661 | Microsoft Docs"
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
  - "CS1661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1661"
ms.assetid: 162d5736-ca3c-4a09-a5d9-a19da3d5bf24
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1661
Невозможно преобразовать блок анонимного метода в тип делегата "тип\_делегата", так как типы параметров указанного блока не соответствуют типам параметров делегата  
  
 Эта ошибка возникает, если в определении анонимного метода типы параметров анонимного метода не соответствуют типам параметров делегата. Проверьте число параметров, типы параметров и все параметры ref и out, а также точное соответствие.  
  
 Следующий пример приводит к возникновению ошибки CS1661:  
  
```  
// CS1661.cs delegate void MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(string s) { };  // CS1661 } }  
```