---
title: "Ошибка компилятора CS1542 | Microsoft Docs"
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
  - "CS1542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1542"
ms.assetid: d7f60aa2-6645-472c-ac12-fa57a09fbd87
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1542
Невозможно добавить "библиотека DLL" в эту сборку, так как он уже находится в сборке; используйте параметр "\/R"  
  
 Файл, на который ссылается параметр компилятора [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option), не был собран с параметром [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md); используйте параметр [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) для создания ссылки на файл в этой компиляции.