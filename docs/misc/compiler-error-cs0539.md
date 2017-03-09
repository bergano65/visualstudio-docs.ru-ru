---
title: "Ошибка компилятора CS0539 | Microsoft Docs"
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
  - "CS0539"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0539"
ms.assetid: 41b8975c-abd1-4a36-98a4-8efa5fb0502a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0539
"член" в явном объявлении интерфейса не является членом интерфейса  
  
 Была предпринята попытка явного объявления члена [интерфейса](/dotnet/csharp/language-reference/keywords/interface), который не существует. Необходимо либо удалить объявление, либо изменить его таким образом, чтобы оно ссылалось на допустимый член интерфейса.  
  
 Следующий пример приводит к возникновению ошибки CS0539:  
  
```  
// CS0539.cs namespace x { interface I { void m(); } public class clx : I { void I.x()   // CS0539 { } public static int Main() { return 0; } } }  
```