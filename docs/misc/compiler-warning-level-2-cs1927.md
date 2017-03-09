---
title: "Предупреждение компилятора (уровень&#160;2) CS1927 | Microsoft Docs"
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
  - "CS1927"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1927"
ms.assetid: 32b4e58f-668c-4596-9529-7f3a293ff4ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;2) CS1927
Пропуск \/win32manifest для модуля, так как он применяется только для сборок  
  
 Манифест win32 применяется только на уровне сборки. Модуль будет скомпилирован, но не будет иметь манифеста.  
  
### Исправление ошибки  
  
1.  Удалите параметр **\/win32manifest option**.  
  
2.  Скомпилируйте код как сборку.  
  
## Пример  
 Приведенный ниже пример приводит к возникновению предупреждения CS1927 при компиляции с использованием как параметра **\/target:module**, так и параметра **\/win32manifest**.  
  
```  
// cs1927.cs // Compile with: /target:module /win32manifest using System; class ManifestWithModule { static int Main() { return 1; } }  
```  
  
## См. также  
 [\/win32manifest \(Import a Custom Win32 Manifest File\)](/dotnet/csharp/language-reference/compiler-options/win32manifest-compiler-option)   
 [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)