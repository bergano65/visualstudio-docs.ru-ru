---
title: "Ошибка компилятора CS0842 | Microsoft Docs"
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
  - "CS0842"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0842"
ms.assetid: 93a8b333-efc4-40c7-ae53-5264f721a74f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0842
Автоматически реализованные свойства не могут использоваться в типах, помеченных StructLayout\(LayoutKind.Explicit\).  
  
 Автоматически реализуемые свойства имеют резервные поля, предоставленные компилятором, и такое поле недоступно для исходного кода. Таким образом, они не совместимы с <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
### Исправление ошибки  
  
1.  Сделайте свойство обычным свойством, в котором можно предоставлять тела методов доступа.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0842:  
  
```  
// cs0842.cs using System; using System.Runtime.InteropServices; namespace TestNamespace { [StructLayout(LayoutKind.Explicit)] struct Str { public int Num // CS0842 { get; set; } static int Main() { return 1; } } }  
```