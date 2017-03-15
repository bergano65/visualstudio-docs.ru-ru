---
title: "Ошибка компилятора CS0711 | Microsoft Docs"
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
  - "CS0711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0711"
ms.assetid: 3a5a6d90-e15d-4808-a7a6-c85fd011a0d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0711
Статические классы не могут содержать деструкторы.  
  
 Для статических классов нельзя создавать экземпляры, поэтому для них не нужны конструкторы и деструкторы. Чтобы избежать возникновения этой ошибки, удалите деструкторы из статических классов или, если все же необходимо создавать и уничтожать экземпляры, сделайте соответствующие классы нестатическими.  
  
 Следующий пример приводит к возникновению ошибки CS0711:  
  
```  
// CS0711.cs public static class C { ~C()  // CS0711 { } public static void Main() { } }  
```