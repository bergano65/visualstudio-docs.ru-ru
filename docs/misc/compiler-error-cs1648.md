---
title: "Ошибка компилятора CS1648 | Microsoft Docs"
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
  - "CS1648"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1648"
ms.assetid: 5cf1bc84-cd18-4df2-942f-1cc17eabacd6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1648
Модификация членов доступного только для чтения поля "идентификатор" возможна только в конструкторе или в инициализаторе переменной  
  
 Эта ошибка возникает при попытке изменить член поля, доступного только для чтения, где нельзя вносить изменения. Чтобы устранить эту ошибку, при назначении полям, доступным только для чтения, ограничьтесь конструктором или инициализатором переменных или удалите ключевое слово readonly из объявления поля.  
  
 Следующий пример приводит к возникновению ошибки CS1648:  
  
```  
// CS1648.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void Main() { Outer outer = new Outer(); outer.inner.i = 1;  // CS1648 } }  
```