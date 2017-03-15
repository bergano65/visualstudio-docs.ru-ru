---
title: "Ошибка компилятора CS0455 | Microsoft Docs"
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
  - "CS0455"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0455"
ms.assetid: a09840ac-ad8c-4c9c-868e-b83d937c7047
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0455
Параметр типа "Имя параметра типа" наследует конфликтующие ограничения "Имя ограничения 1" и "Имя ограничения 2"  
  
 Как правило, эта ошибка возникает, если ограничения устанавливаются таким образом, что параметр типа наследуется от двух несвязанных классов либо одновременно от ограничения типа класса или ссылки и ограничения типа значения или `struct`. Чтобы устранить эту ошибку, разрешите конфликт в иерархии наследования.  
  
## Пример  
 Приведенный ниже код вызывает ошибку CS0455.  
  
```  
// CS0455.cs using System; public class GenericsErrors { public class B { } public class B2 { } public class G6<T> where T : B { public class N<U> where U : B2, T { } } // CS0455 }  
```