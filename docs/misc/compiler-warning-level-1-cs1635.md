---
title: "Предупреждение компилятора (уровень&#160;1) CS1635 | Microsoft Docs"
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
  - "CS1635"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1635"
ms.assetid: e1795880-f7ea-4dca-b15b-4ba549d7ed78
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS1635
Невозможно возобновить предупреждение "код предупреждения", поскольку оно было глобально отключено  
  
 Это предупреждение возникает, если используется параметр **\/nowarn** командной строки или в параметрах проекта отключены предупреждения компилятора для всего блока компиляции, но при этом для попытки восстановления этого предупреждения используется директива `#pragma warning restore`. Для устранения этой ошибки удалите из командной строки параметр \/nowarn, измените параметры проекта либо удалите директиву `#pragma warning restore` для предупреждений, отключаемых с использованием командной строки или параметров проекта. Дополнительные сведения см. в разделе [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning).  
  
 Следующий пример приводит к возникновению предупреждения CS1635:  
  
```  
// CS1635.cs // compile with: /w:1 /nowarn:162 enum MyEnum {one=1,two=2,three=3}; class MyClass { public static void Main() { #pragma warning disable 162 if (MyEnum.three == MyEnum.two) System.Console.WriteLine("Duplicate"); #pragma warning restore 162 } }  
```