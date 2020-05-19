---
title: DebugBreak и __debugbreak | Документация Майкрософт
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 097405f98d1a80b8605b6773bdc675ff2c4ab773
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404656"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak и __debugbreak
Вызов функции [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Win32 или встроенной функции [__debugbreak](/cpp/intrinsics/debugbreak) можно разместить в любом месте кода. Вызов `DebugBreak` или `__debugbreak` эквивалентен установке точки останова в этом месте программы.

 Поскольку `DebugBreak` — это системная функция, на компьютере должны быть установлены системные отладочные символы, гарантирующие правильное отображение информации стека вызовов после приостановки выполнения. В противном случае сведения стека вызовов, отображаемые в отладчике, могут выйти за пределы одного кадра. При использовании `__debugbreak` символы не требуются.

## <a name="see-also"></a>См. также
- [Встроенные инструкции компилятора](/cpp/intrinsics/compiler-intrinsics)
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)
- [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
