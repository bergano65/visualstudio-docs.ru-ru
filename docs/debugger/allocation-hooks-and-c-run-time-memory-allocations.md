---
title: Ловушки выделения и выделения памяти CRT
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be75b4d3e83ed297f31e9015c7ba082c0611206d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851623"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Ловушки выделения и выделения памяти CRT
Для функций-ловушек выделения есть важное ограничение: они должны пропускать блоки `_CRT_BLOCK`. Это выделения памяти, создаваемые внутри библиотеки CRT ее функциями при любом вызове функций CRT, выделяющих внутреннюю память. Вы можете исключить блоки `_CRT_BLOCK` из обработки путем добавления в начало функции-ловушки выделения следующего кода:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Если ловушка обрабатывает блоки `_CRT_BLOCK`, то любая вызываемая в ней функция CRT может привести к выполнению в программе бесконечного цикла. Например, `printf` осуществляет внутреннее выделение. Если код ловушки вызывает `printf`, получающееся выделение приведет к повторному вызову ловушки, где снова будет вызван **printf**, и так далее до переполнения стека. Если нужен отчет об операциях выделения `_CRT_BLOCK`, есть способ обойти это ограничение — для форматирования и вывода использовать функции Windows API вместо функций CRT. Так как функции API-интерфейсов Windows не используют кучу библиотеки CRT, они не могут привести к выполнению в приложении бесконечного цикла.

Если посмотреть на исходные CRT-файлы, то можно увидеть, что стандартная функция-ловушка выделения **CrtDefaultAllocHook** (возвращающая просто значение **TRUE**) находится в собственном отдельном файле DBGHOOK.C. Если нужно, чтобы ловушка выделения вызывалась даже для выделений, сделанных в коде запуска CRT, выполняющемся перед функцией приложения **main**, то можно вместо использования [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) заменить эту стандартную функцию одной из своих.

## <a name="see-also"></a>См. также
- [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)
