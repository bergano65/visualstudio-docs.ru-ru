---
title: DebugBreak и __debugbreak | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 83128e4d5bd274013db1e7195e8182d021c257d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak и __debugbreak
Можно вызывать функции DebugBreak Win32 или [__debugbreak](/cpp/intrinsics/debugbreak) разместить в любом месте в коде. Вызов `DebugBreak` или `__debugbreak` эквивалентен установке точки останова в этом месте программы.  
  
 Поскольку `DebugBreak` — это системная функция, на компьютере должны быть установлены системные отладочные символы, гарантирующие правильное отображение информации стека вызовов после приостановки выполнения. В противном случае сведения стека вызовов, отображаемые в отладчике, могут выйти за пределы одного кадра. При использовании `__debugbreak` символы не требуются.  
  
## <a name="see-also"></a>См. также  
 [Встроенные объекты компилятора](/cpp/intrinsics/compiler-intrinsics)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Укажите символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)