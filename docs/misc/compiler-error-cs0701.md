---
title: "Ошибка компилятора CS0701 | Microsoft Docs"
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
  - "CS0701"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0701"
ms.assetid: eb844e31-00bd-468d-9f77-11d10a4ef120
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0701
"идентификатор" не является допустимым ограничением. Тип, использованный в качестве ограничения, должен быть интерфейсом, незапечатанным классом или параметром типа.  
  
 Эта ошибка возникает при использовании запечатанного типа в качестве ограничения. Чтобы устранить эту ошибку, используйте в качестве ограничений только незапечатанные типы.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0701.  
  
```  
// CS0701.cs // compile with: /target:library class C<T> where T : System.String {}   // CS0701 class D<T> where T : System.Attribute {}   // OK  
```