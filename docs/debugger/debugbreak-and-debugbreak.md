---
title: "DebugBreak и __debugbreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DebugBreak"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "точки останова, DebugBreak - функция"
  - "DebugBreak - функция"
  - "отладка [C++], DebugBreak - функция"
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# DebugBreak и __debugbreak
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Вызов функции DebugBreak Win32 или встроенной функции [\_\_debugbreak](/visual-cpp/intrinsics/debugbreak) можно разместить в любом месте кода.  Вызов `DebugBreak` или `__debugbreak` эквивалентен установке точки останова в этом месте программы.  
  
 Поскольку `DebugBreak` — это системная функция, на компьютере должны быть установлены системные отладочные символы, гарантирующие правильное отображение информации стека вызовов после приостановки выполнения.  В противном случае сведения стека вызовов, отображаемые в отладчике, могут выйти за пределы одного кадра.  При использовании `__debugbreak` символы не требуются.  
  
## См. также  
 [Встроенные объекты компилятора](/visual-cpp/intrinsics/compiler-intrinsics)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Указание файлов символов \(.pdb\) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)