---
title: "Ошибка компилятора CS0610 | Microsoft Docs"
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
  - "CS0610"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0610"
ms.assetid: 6cdce74c-5c00-4539-9df1-32be70e9912d
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0610
Поле или свойство не может иметь тип "тип"  
  
 Имеется несколько типов, которые нельзя использовать в качестве полей или свойств. В число этих типов входят **System.ArgIterator** и **System.TypedReference**.  
  
 В приведенном ниже примере ошибка CS0610 возникает в результате использования типа **System.TypedReference** для поля.  
  
```  
// CS0610.cs public class MainClass { System.TypedReference i;   // CS0610 public static void Main () { } public static void Test(System.TypedReference i)   // OK { } }  
```