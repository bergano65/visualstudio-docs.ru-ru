---
title: "Ошибка компилятора CS1650 | Microsoft Docs"
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
  - "CS1650"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1650"
ms.assetid: 251a3a67-6e56-4795-874a-d54610c70595
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1650
Присваивание значений полям статического поля "идентификатор", доступного только для чтения, допускается только в статическом конструкторе или инициализаторе переменных  
  
 Эта ошибка возникает при попытке изменить член поля, который доступен только для чтения и является статическим, где нельзя вносить изменения. Чтобы устранить эту ошибку, при назначении полям, доступным только для чтения, ограничьтесь конструктором или инициализатором переменных или удалите ключевое слово `readonly` из объявления поля.  
  
```  
// CS1650.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void Main() { Outer.inner.i = 1;  // CS1650 } }  
```