---
title: Функции-ловушки выделения | Документация Майкрософт
description: Сведения об использовании функции-ловушки выделения, устанавливаемой с помощью _CrtSetAllocHook, если необходимо выполнить отладку в Visual Studio во время выполнения C (CRT).
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c032ca57e5a046a9f2dd2295226263ffe20f99e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858011"
---
# <a name="allocation-hook-functions"></a>Функции-ловушки выделения
Функции-ловушки выделения, установленные с помощью [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), вызываются всякий раз при выделении, перераспределении или освобождении памяти. Этот тип ловушек можно использовать для различных целей. Используйте их, например, для проверки, как приложение обрабатывает ситуации недостатка памяти, или для оценки шаблонов выделения, или для регистрации данных о выделении для дальнейшего анализа.

> [!NOTE]
> Следует знать об ограничениях функций библиотеки CRT в функциях-ловушках выделения, описанных в разделе [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Функция-ловушка выделения должна иметь следующий пример:

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

 Когда библиотека CRT вызывает ловушку, аргумент *nAllocType* показывает, какого вида операция выделения будет выполнена ( **_HOOK_ALLOC**, **_HOOK_REALLOC** или _ **HOOK_FREE)** . В случае освобождения или перераспределения, `pvData` содержит указатель на пользовательскую часть освобождаемого блока. Однако в случае выделения памяти этот указатель пуст, так как выделение еще не произошло. Остальные аргументы содержат размер запрашиваемого выделения, его тип блока, номер последующего запроса, связанный с выделением запроса, и указатель на имя файла. Если он доступен, аргументы также включают номер строки, в которой было выполнено выделение. После того как функция-ловушка выполнит анализ и другие запрограммированные автором действия, она должна вернуть или значение **TRUE**, означающее, что операция выделения может продолжаться, или значение **FALSE** в случае предполагаемого сбоя операции. Простая ловушка этого типа может проверить количество выделенной до настоящего момента памяти и вернуть **FALSE** в случае превышения лимита. В таком случае в приложении могут возникать ошибки выделения памяти, которые обычно возникают только при большой нехватке доступной памяти. Более сложные ловушки могут отслеживать структуру выделения, анализировать использование памяти или сообщать о возникновении какой-либо определенной ситуации.

## <a name="see-also"></a>См. также

- [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)