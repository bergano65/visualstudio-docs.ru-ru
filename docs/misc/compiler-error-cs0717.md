---
title: "Ошибка компилятора CS0717 | Microsoft Docs"
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
  - "CS0717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0717"
ms.assetid: 1976e82a-d048-4f13-a95a-a7f4e3cd7038
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0717
"статический класс": статические классы не могут использоваться как ограничения  
  
 Статические классы не могут быть расширены, поскольку они содержат только статические элементы и не содержат члены экземпляров. Раз они не могут быть расширены, это делает их бесполезными в качестве параметров типов и ограничений, так как не может существовать ни один тип, являющийся специализацией статического класса.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0717:  
  
```  
// CS0717.cs public static class SC { public static void F() { } } public class G<T> where T : SC  // CS0717 { public static void Main() { } }  
```