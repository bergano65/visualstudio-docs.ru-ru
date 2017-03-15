---
title: "Ошибка компилятора CS1688 | Microsoft Docs"
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
  - "CS1688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1688"
ms.assetid: e15672a1-2570-4e65-99fc-7acc190ae643
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1688
Невозможно преобразовать блок анонимного метода без списка параметров в делегат "делегат", поскольку он имеет один или несколько выходных параметров  
  
 В большинстве случаев компилятор позволяет опускать параметры в блоке анонимного метода. Эта ошибка возникает при отсутствии списка параметров в блоке анонимного метода и при наличии параметра `out` у делегата. Компилятор не допускает возникновение такой ситуации, так как игнорирование имеющегося параметра `out` почти наверняка вызовет появление ошибок.  
  
## Пример  
 Приведенный ниже код вызывает ошибку CS1688.  
  
```  
// CS1688.cs using System; delegate void OutParam(out int i); class ErrorCS1676 { static void Main() { OutParam o; o = delegate  // CS1688 // Try this instead: // o = delegate(out int i) { Console.WriteLine(""); }; } }  
```