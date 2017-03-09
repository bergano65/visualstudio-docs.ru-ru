---
title: "Ошибка компилятора CS0752 | Microsoft Docs"
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
  - "CS0752"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0752"
ms.assetid: f9a373d6-31ed-42db-8206-80cbe9b8c546
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0752
Разделяемый метод не может иметь параметры out.  
  
 Разделяемый метод не может иметь параметр [out](/dotnet/csharp/language-reference/keywords/out). Параметры out запрещены, поскольку при удалении компилятором разделяемого метода нет никакой гарантии, что параметр out когда\-либо будет назначен.  
  
### Исправление ошибки  
  
1.  Удалите модификатор out из параметра и используйте вместо него возвращаемое значение метода либо удалите модификатор partial из объявления метода.  
  
## Пример  
 В следующем коде возникает ошибка CS0752:  
  
```  
// cs0752.cs public partial class C { partial void Part(out int num); // CS0752 // try the following line instead // partial void Part(int num); public static int Main() { return 1; } }  
```  
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)