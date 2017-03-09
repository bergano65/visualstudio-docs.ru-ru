---
title: "Ошибка компилятора CS2036 | Microsoft Docs"
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
  - "CS2036"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2036"
ms.assetid: 44b73be4-b792-4735-bdbd-bd757ab22683
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS2036
С параметром \/pdb необходимо использовать также параметра \/debug.  
  
 Файлы базы данных программы создаются только для отладочных сборок. Таким образом, параметр **\/pdb** не имеет смысла в коммерческой сборке.  
  
### Исправление ошибки  
  
-   Добавьте параметр компилятора **\/debug**.  
  
-   Удалите параметр компилятора **\/pdb**.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS2036 при компиляции с параметром **\/pdb**, но без параметра \/debug.  
  
```  
// cs2036.cs // Compile with: /pdb // CS2036 class Test { public static int Main() { return 1; } }  
```  
  
## См. также  
 [\/pdb \(Specify Debug Symbol File\)](/dotnet/csharp/language-reference/compiler-options/pdb-compiler-option)   
 [\/debug \(Emit Debugging Information\)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)