---
title: "Ошибка компилятора CS0531 | Microsoft Docs"
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
  - "CS0531"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0531"
ms.assetid: 54c2a98b-84e3-481a-a934-7cd6dffa7677
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0531
"член": члены интерфейса не могут иметь определения  
  
 Методы, объявленные в [интерфейсе](/dotnet/csharp/language-reference/keywords/interface), должны быть реализованы в классе, который наследует от него, а не в самом интерфейсе.  
  
 В следующем примере возникает ошибка CS0531:  
  
```  
// CS0531.cs namespace x { public interface clx { int xclx()   // CS0531, cannot define xclx // Try the following declaration instead: // int xclx(); { return 0; } } public class cly { public static void Main() { } } }  
```