---
title: "Ошибка компилятора CS0694 | Microsoft Docs"
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
  - "CS0694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0694"
ms.assetid: 048615e4-4599-4726-b5db-55322ccc936f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0694
Параметр типа "идентификатор" совпадает с именем вмещающего типа или метода  
  
 Вы должны использовать другое имя для параметра типа, так как имя параметра типа не может совпадать с именем типа или метода, который содержит параметр типа.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS0694.  
  
```  
// CS0694.cs // compile with: /target:library class C<C> {}   // CS0694  
```  
  
## Пример  
 Помимо описанного выше случая с универсальным классом эта ошибка может возникнуть и с методом:  
  
```  
// CS0694_2.cs // compile with: /target:library class A { public void F<F>(F arg);   // CS0694 }  
```