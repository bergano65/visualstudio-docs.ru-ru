---
title: "Ошибка компилятора CS0718 | Microsoft Docs"
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
  - "CS0718"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0718"
ms.assetid: f18ea7b7-7495-4039-9876-409e9fe98ba1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0718
"тип": статические типы не могут использоваться как аргументы типа  
  
 Поскольку невозможно создать экземпляры статического типа, его нельзя использовать как универсальный аргумент. Чтобы устранить эту ошибку, удалите статический тип из универсального аргумента.  
  
## Пример  
 В следующем примере возникает ошибка CS0718:  
  
```  
// CS0718.cs public static class SC { public static void F() { } } public class G<T> { } public class CMain { public static void Main() { G<SC> gsc = new G<SC>();  // CS0718 } }  
```