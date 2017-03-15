---
title: "Ошибка компилятора CS1109 | Microsoft Docs"
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
  - "CS1109"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1109"
ms.assetid: bebe56b8-3831-4ebb-a49e-e0364b4c11a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1109
Методы расширения должны быть определены в статическом классе верхнего уровня; "имя" является вложенным классом.  
  
 Методы расширения не могут быть определены во вложенных классах.  
  
## Пример  
 В следующем примере возникает ошибка CS1109, так как класс `Extension` вложен в класс `Out`.  
  
```  
// cs1109.cs public class Test { } static class Out { static class Extension { static void ExtMethod(this Test c) // CS1109 { } } }  
```  
  
## См. также  
 [Методы расширения](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)