---
title: "Ошибка компилятора CS1677 | Microsoft Docs"
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
  - "CS1677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1677"
ms.assetid: 8c974669-15c6-4010-8b02-21021bed5af9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1677
Параметр "число" не должен объявляться с ключевым словом "ключевое\_слово"  
  
 Эта ошибка возникает, если модификатор типа параметра в анонимном методе не соответствует модификатору, используемому в объявлении делегата, к которому выполняется приведение метода.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1677:  
  
```  
// CS1677.cs delegate void D(int i); class Errors { static void Main() { D d = delegate(out int i) { };   // CS1677 // To resolve, use the following line instead: // D d = delegate(int i) { }; D d = delegate(ref int j){}; // CS1677 // To resolve, use the following line instead: // D d = delegate(int j){}; } }  
```