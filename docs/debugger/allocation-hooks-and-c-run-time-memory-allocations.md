---
title: Ловушки выделения и выделения памяти времени выполнения C | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e4c631b72ae9b12f77daf2ddd49919651c0b3e5
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433110"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Ловушки выделения и выделения памяти CRT
Очень важное условие для функций-ловушек выделения — что они должны явно обрабатывать `_CRT_BLOCK` блоков. Эти блоки являются выделения памяти, сделанные внутри функции библиотеки времени выполнения C при вызове функций библиотеки CRT, выделяющих внутреннюю память. Вы можете игнорировать `_CRT_BLOCK` функции-ловушки блоков, включая код folloiwng в начале выделения:  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Если ловушка выделения не обходит `_CRT_BLOCK` блокируется, а затем любой функции библиотеки времени выполнения C, вызываемая в ней ловушка в программе бесконечного цикла. Например, `printf` осуществляет внутреннее выделение. Если код ловушки вызывает `printf`, то получающееся выделение приведет к повторному вызову ловушки вызываться снова, который вызовет **printf** еще раз, и так далее до переполнения стека. Если нужен отчет об операциях выделения `_CRT_BLOCK`, есть способ обойти это ограничение — для форматирования и вывода использовать функции Windows API вместо функций CRT. Так как API-интерфейсы Windows не используют кучу библиотеки времени выполнения C, они не привести к выполнению в бесконечном цикле.  
  
 Если посмотреть на исходные файлы библиотеки времени выполнения, вы увидите, что функция-ловушка выделения по умолчанию **CrtDefaultAllocHook** (возвращающая просто значение **TRUE**), находится в отдельном файле свои собственные, DBGHOOK. C. Если необходимо, чтобы ловушка выделения для вызова даже для выделений, сделанных в коде запуска во время выполнения, выполняется перед выполнением приложения **основной** функции, можно заменить эту стандартную функцию одной из своих, а не с помощью [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
