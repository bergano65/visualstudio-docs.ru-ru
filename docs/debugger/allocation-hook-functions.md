---
title: Функции-ловушки выделения | Документация Майкрософт
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd2900544fe2c33cfaaf9d1a0da5d4ff1ac41ab4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616798"
---
# <a name="allocation-hook-functions"></a>Функции-ловушки выделения
Функции-ловушки выделения, установленные с помощью [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), вызываются всякий раз при выделении, перераспределить или освобождении памяти. Можно использовать этот тип ловушек для различных целей. Использовать для тестирования, как приложение обрабатывает ситуации недостатка памяти, например, для оценки шаблонов выделения, или регистрации данных о выделении для дальнейшего анализа.

> [!NOTE]
>  Следует знать об ограничениях функций библиотеки CRT в функциях-ловушках выделения, описанных в разделе [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Функция-ловушка выделения должна иметь прототип как в следующем примере:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 Указатель, который передается [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), имеет тип **_CRT_ALLOC_HOOK**, как определено в CRTDBG.H:

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Когда библиотека CRT вызывает ловушку, *nAllocType* аргумент указывает, какие выделения операции будет осуществляться (**_HOOK_ALLOC**, **_HOOK_REALLOC**, или **_HOOK_FREE**). В бесплатной или перераспределения `pvData` содержит указатель на статье пользователя освобождаемого блока. Тем не менее для выделения памяти этот указатель имеет значение null, так как не произошла операция выделения. Остальные аргументы содержат размер запрашиваемого выделения, его тип блока, номер последующего запроса связанный с ней указатель на имя файла. Если он доступен, аргументы также включают номер строки, в которой было сделано выделение. После того как функция-ловушка выполнит анализ и другие запрограммированные автором действия, она должна вернуть или значение **TRUE**, означающее, что операция выделения может продолжаться, или значение **FALSE** в случае предполагаемого сбоя операции. Простая ловушка этого типа может проверить количество выделенной до настоящего момента памяти и вернуть **FALSE** в случае превышения лимита. В таком случае в приложении могут возникать ошибки выделения памяти, которые обычно возникают только при большой нехватке доступной памяти. Более сложные ловушки могут отслеживать структуру выделения, анализировать использование памяти или сообщать о возникновении какой-либо определенной ситуации.

## <a name="see-also"></a>См. также раздел

- [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)