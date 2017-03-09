---
title: "Ошибка компилятора CS0646 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0646"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0646"
ms.assetid: 48ea306f-b4a0-4988-8d2b-ca9d38e9bdad
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0646
Невозможно указать атрибут DefaultMember для типа, содержащего индексатор.  
  
 Если класс или другой тип указывает **System.Reflection.DefaultMemberAttribute**, он не может содержать индексатор. Дополнительные сведения см. в разделе [Свойства](/dotnet/csharp/programming-guide/classes-and-structs/properties).  
  
 В следующем примере возникает ошибка CS0646.  
  
```  
// CS0646.cs // compile with: /target:library [System.Reflection.DefaultMemberAttribute("x")]   // CS0646 class MyClass { public int this[int index]   // an indexer { get { return 0; } } public int x = 0; } // OK [System.Reflection.DefaultMemberAttribute("x")] class MyClass2 { public int prop { get { return 0; } } public int x = 0; } class MyClass3 { public int this[int index]   // an indexer { get { return 0; } } public int x = 0; }  
```