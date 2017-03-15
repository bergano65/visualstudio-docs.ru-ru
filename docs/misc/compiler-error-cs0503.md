---
title: "Ошибка компилятора CS0503 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0503"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0503"
ms.assetid: 12a337c9-8c5d-473d-8ce6-057b2c7e7935
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0503
Абстрактный метод "метод" не может быть помечен как виртуальный  
  
 Излишне одновременно помечать метод как [абстрактный](/dotnet/csharp/language-reference/keywords/abstract) и как [виртуальный](/dotnet/csharp/language-reference/keywords/virtual), потому что подразумевается, что **абстрактный** метод является **виртуальным**.  
  
 Следующий пример приводит к возникновению ошибки CS0503:  
  
```  
// CS0503.cs namespace x { abstract public class clx { abstract virtual public void f();   // CS0503 } }  
```