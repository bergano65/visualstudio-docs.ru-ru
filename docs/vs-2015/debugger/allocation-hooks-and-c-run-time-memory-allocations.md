---
title: Ловушки выделения и выделения памяти времени выполнения C | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3dbb9f2640d3da71566b8c8839b413943927af2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569173"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Ловушки выделения и выделения памяти CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ловушки выделения и выделения памяти времени выполнения C](https://docs.microsoft.com/visualstudio/debugger/allocation-hooks-and-c-run-time-memory-allocations).  
  
Очень важное условие для функций-ловушек выделения — то, что они не должны явно обрабатывать блоки `_CRT_BLOCK` (выделения памяти, сделанные внутри библиотеки CRT ее функциями) при любом вызове функций CRT, выделяющих внутреннюю память. Блоки `_CRT_BLOCK` можно исключить из обработки путем добавления в начало функции-ловушки выделения следующего кода:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Если ловушка обрабатывает блоки `_CRT_BLOCK`, то любая вызываемая в ней функция CRT может привести к выполнению в программе бесконечного цикла. Например, `printf` осуществляет внутреннее выделение. Если код ловушки вызывает `printf`, а затем получающееся выделение приведет к повторному вызову ловушки вызываться снова, который вызовет **printf** еще раз, и так далее до переполнения стека. Если нужен отчет об операциях выделения `_CRT_BLOCK`, есть способ обойти это ограничение — для форматирования и вывода использовать функции Windows API вместо функций CRT. Поскольку функции Windows API не используют кучу библиотеки CRT, они не могут привести к выполнению в приложении бесконечного цикла.  
  
 Если посмотреть на исходные файлы библиотеки времени выполнения, вы увидите, что функция-ловушка выделения по умолчанию **CrtDefaultAllocHook** (возвращающая просто значение **TRUE**), находится в отдельном файле свои собственные, DBGHOOK. C. Если необходимо, чтобы ловушка выделения для вызова даже для выделений, сделанных в коде запуска во время выполнения, выполняется перед выполнением приложения **основной** функции, можно заменить эту стандартную функцию одной из своих, а не с помощью [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



