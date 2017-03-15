---
title: "Ошибка компилятора CS0439 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0439"
ms.assetid: 5cbac869-1b1b-45f9-98c8-38c17348035f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0439
Объявление внешнего псевдонима должно предшествовать всем другим элементам, определенным в пространстве имен.  
  
 Эта ошибка возникает, когда объявление `extern` следует после чего\-либо еще, например объявления `using`, в том же пространстве имен. Объявления `extern` должны задаваться до всех других элементов пространства имен.  
  
## Пример  
 В следующем примере возникает ошибка CS0439:  
  
```  
// CS0439.cs using System; extern alias MyType;   // CS0439 // To resolve the error, make the extern alias the first line in the file. public class Test { public static void Main() { } }  
```