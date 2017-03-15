---
title: "Ошибка компилятора CS0274 | Microsoft Docs"
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
  - "CS0274"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0274"
ms.assetid: bbd2d64e-a756-4713-b9ed-711d50b65e00
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0274
Не удается определить модификаторы доступа для обоих методов доступа свойства или индексатора "свойство\/индексатор".  
  
 Эта ошибка возникает при объявлении свойства или индексатора с модификаторами доступа в обоих его методах доступа. Чтобы устранить эту ошибку, используйте модификатор доступа только в одном из двух методов доступа. Дополнительные сведения см. в разделе [Доступность методов доступа](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
 Следующий пример приводит к возникновению ошибок CS0274:  
  
```  
// CS0274.cs public class MyClass { public int Property   // CS0274 { public get { return 0; } protected set { } } }  
```