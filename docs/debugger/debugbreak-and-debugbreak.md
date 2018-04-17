---
title: DebugBreak и __debugbreak | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d76b4a08c90b3ae37832da97e0615282c0f11d67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak и __debugbreak
Можно вызывать функции DebugBreak Win32 или [__debugbreak](/cpp/intrinsics/debugbreak) разместить в любом месте в коде. Вызов `DebugBreak` или `__debugbreak` эквивалентен установке точки останова в этом месте программы.  
  
 Поскольку `DebugBreak` — это системная функция, на компьютере должны быть установлены системные отладочные символы, гарантирующие правильное отображение информации стека вызовов после приостановки выполнения. В противном случае сведения стека вызовов, отображаемые в отладчике, могут выйти за пределы одного кадра. При использовании `__debugbreak` символы не требуются.  
  
## <a name="see-also"></a>См. также  
 [Встроенные объекты компилятора](/cpp/intrinsics/compiler-intrinsics)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Укажите символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)