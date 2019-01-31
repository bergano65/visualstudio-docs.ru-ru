---
title: Ловушки выделения и выделения памяти времени выполнения C | Документация Майкрософт
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
ms.openlocfilehash: f9432eab55f22bcf18266a10e4e1616997ed8c4a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924182"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Ловушки выделения и выделения памяти CRT
Очень важное условие для функций-ловушек выделения — что они должны явно обрабатывать `_CRT_BLOCK` блоков. Эти блоки являются выделения памяти, сделанные внутри функции библиотеки времени выполнения C при вызове функций библиотеки CRT, выделяющих внутреннюю память. Вы можете игнорировать `_CRT_BLOCK` функции-ловушки блоков, включив следующий код в начало выделения:  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Если ловушка выделения не обходит `_CRT_BLOCK` блокируется, а затем любой функции библиотеки времени выполнения C, вызываемая в ней ловушка в программе бесконечного цикла. Например, `printf` осуществляет внутреннее выделение. Если код ловушки вызывает `printf`, получающееся выделение приведет к повторному вызову ловушки, где снова будет вызван **printf**, и так далее до переполнения стека. Если нужен отчет об операциях выделения `_CRT_BLOCK`, есть способ обойти это ограничение — для форматирования и вывода использовать функции Windows API вместо функций CRT. Так как API-интерфейсы Windows не используют кучу библиотеки времени выполнения C, они не привести к выполнению в бесконечном цикле.  
  
 Если посмотреть на исходные CRT-файлы, то можно увидеть, что стандартная функция-ловушка выделения **CrtDefaultAllocHook** (возвращающая просто значение **TRUE**) находится в собственном отдельном файле DBGHOOK.C. Если нужно, чтобы ловушка выделения вызывалась даже для выделений, сделанных в коде запуска CRT, выполняющемся перед функцией приложения **main**, то можно вместо использования [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) заменить эту стандартную функцию одной из своих.  
  
## <a name="see-also"></a>См. также раздел  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
