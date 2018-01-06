---
title: "Функции-ловушки выделения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fe5ac5ec207bb52884c097d1562a85a3414ba7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="allocation-hook-functions"></a>Функции-ловушки выделения
Функции-ловушки выделения, установленные с помощью [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), вызывается каждый раз при выделении, перераспределении или освобождении памяти. Этот тип ловушек может применяться для различных целей. Используйте их, например, для проверки, как приложение обрабатывает ситуации недостатка памяти, или для оценки шаблонов выделения, или для регистрации данных о выделении для дальнейшего анализа.  
  
> [!NOTE]
>  Помните о ограничениях функций библиотеки времени выполнения C в функции-ловушки выделения, описанных в [ловушки выделения и выделения памяти времени выполнения C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Функция-ловушка выделения должна иметь следующий прототип:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Указатель, передаваемый [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) относится к типу **_CRT_ALLOC_HOOK**, как определено в CRTDBG. H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Когда библиотеки CRT вызывает к выполнению *nAllocType* аргумент указывает, какие выделения операция будет выполняться (**_HOOK_ALLOC**, **_HOOK_REALLOC**, или **_HOOK_FREE**). В случае освобождения или перераспределения, `pvData` содержит указатель на пользовательскую часть освобождаемого блока. Однако в случае выделения памяти этот указатель пуст, так как выделение еще не произошло. Остальные аргументы содержат размер запрашиваемого выделения, его тип блока, номер последующего запроса, связанный с выделением запроса, и указатель на имя файла и номер строки, в которой было сделано выделение (если доступно). Когда функция-ловушка выполнит анализ и другие запрограммированные автором, она должна вернуть или **TRUE**, означает, что операция выделения может продолжаться, или **FALSE**, означающее, Операция должна завершиться ошибкой. Простая ловушка этого типа может проверить количество выделенной до настоящего момента памяти и вернуть **FALSE** случае превышения лимита. В таком случае в приложении могут возникать ошибки выделения памяти, которые обычно возникают только при большой нехватке доступной памяти. Более сложные ловушки могут отслеживать структуру выделения, анализировать использование памяти или сообщать о возникновении какой-либо определенной ситуации.  
  
## <a name="see-also"></a>См. также  
 [Ловушки выделения и выделения памяти времени выполнения C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
