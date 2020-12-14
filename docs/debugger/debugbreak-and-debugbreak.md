---
title: DebugBreak и __debugbreak | Документация Майкрософт
description: Сведения об использовании функции DebugBreak и встроенной функции __debugbreak для принудительного прерывания программы, эквивалентного достижению точки останова.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 376dd75062dc5a78582a23a12e9e025db60b9f3a
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559775"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak и __debugbreak
Вызов функции [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Win32 или встроенной функции [__debugbreak](/cpp/intrinsics/debugbreak) можно разместить в любом месте кода. Вызов `DebugBreak` или `__debugbreak` эквивалентен установке точки останова в этом месте программы.

 Поскольку `DebugBreak` — это системная функция, на компьютере должны быть установлены системные отладочные символы, гарантирующие правильное отображение информации стека вызовов после приостановки выполнения. В противном случае сведения стека вызовов, отображаемые в отладчике, могут выйти за пределы одного кадра. При использовании `__debugbreak` символы не требуются.

## <a name="see-also"></a>См. также
- [Встроенные инструкции компилятора](/cpp/intrinsics/compiler-intrinsics)
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)
- [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
