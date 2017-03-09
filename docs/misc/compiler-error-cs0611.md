---
title: "Ошибка компилятора CS0611 | Microsoft Docs"
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
  - "CS0611"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0611"
ms.assetid: bbd857a0-9454-4438-a21c-fef5bc7eee06
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0611
Элементы массива не могут иметь тип "тип"  
  
 Имеется несколько типов, которые нельзя использовать в качестве типа массива. В число этих типов входит **System.ArgIterator** и **System.TypedReference**.  
  
 В следующем примере ошибка CS0611 возникает в результате использования типа **System.TypedReference** как элемента массива.  
  
```  
// CS0611.cs public class a { public static void Main() { System.TypedReference[] ao = new System.TypedReference [10];   // CS0611 // try the following line instead // int[] ao = new int[10]; } }  
```