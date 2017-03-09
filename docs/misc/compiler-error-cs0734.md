---
title: "Ошибка компилятора CS0734 | Microsoft Docs"
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
  - "CS0734"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0734"
ms.assetid: 9e1b0e49-bfc3-400c-9fd1-37e3c827e656
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0734
Параметр \/moduleassemblyname может использоваться только при сборке модуля.  
  
 Параметр компилятора **\/moduleassemblyname** должен использоваться только при сборке файлов NETMODULE. Дополнительные сведения см. в разделе [\/moduleassemblyname \(Specify Friend Assembly for Module\)](/dotnet/csharp/language-reference/compiler-options/moduleassemblyname-compiler-option).  
  
 Дополнительные сведения о сборке файлов NETMODULE см. в разделе [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md).  
  
## Пример  
 Приведенный ниже пример приводит к возникновению ошибки CS0734. Чтобы устранить ошибку, добавьте параметр **\/target:module** при компиляции.  
  
```  
// CS0734.cs // compile with: /moduleassemblyname:A // CS0734 expected public class Test {}  
```