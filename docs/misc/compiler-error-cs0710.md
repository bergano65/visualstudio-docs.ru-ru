---
title: "Ошибка компилятора CS0710 | Microsoft Docs"
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
  - "CS0710"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0710"
ms.assetid: 753a1a87-f5e5-4758-a960-515069a6c7b0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0710
Статические классы не могут иметь конструкторы экземпляров.  
  
 Для статических классов нельзя создавать экземпляры, поэтому для них не нужны конструкторы. Чтобы избежать возникновения этой ошибки, удалите конструкторы из статических классов или, если все же необходимо создавать экземпляры, сделайте соответствующие классы не статическими.  
  
 Следующий пример приводит к возникновению ошибки CS0710:  
  
```  
// CS0710.cs public static class C { public C()  // CS0710 { } public static void Main() { } }  
```