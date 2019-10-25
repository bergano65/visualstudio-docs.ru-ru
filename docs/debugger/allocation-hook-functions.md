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
ms.openlocfilehash: f684c6c66448fdab2ee7607a81ff7ed769a5e607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745825"
---
# <a name="allocation-hook-functions"></a>Функции-ловушки выделения
Функция-ловушка выделения, установленная с помощью [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), вызывается каждый раз при выделении, повторном выделении или освобождении памяти. Этот тип обработчика можно использовать для различных целей. Используйте его для проверки того, как приложение обрабатывает недостаточные объемы памяти, например для анализа шаблонов выделения, или сведения о выделении журнала для последующего анализа.

> [!NOTE]
> Следует знать об ограничениях функций библиотеки CRT в функциях-ловушках выделения, описанных в разделе [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Функция-ловушка выделения должна иметь прототип, как в следующем примере:

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

 Когда библиотека времени выполнения вызывает обработчик, аргумент *наллоктипе* указывает, какую операцию выделения следует выполнить ( **_HOOK_ALLOC**, **_HOOK_REALLOC**или **_HOOK_FREE**). В свободной или перераспределении `pvData` имеет указатель на пользовательскую статью блока, который должен быть освобожден. Однако при выделении этот указатель имеет значение null, поскольку выделение не произошло. Остальные аргументы содержат требуемый размер выделения, тип блока, номер последовательного запроса, связанный с ним, и указатель на имя файла. Если он доступен, аргументы также включают номер строки, в которой было выполнено выделение. После того как функция-ловушка выполнит анализ и другие запрограммированные автором действия, она должна вернуть или значение **TRUE**, означающее, что операция выделения может продолжаться, или значение **FALSE** в случае предполагаемого сбоя операции. Простая ловушка этого типа может проверить количество выделенной до настоящего момента памяти и вернуть **FALSE** в случае превышения лимита. В таком случае в приложении могут возникать ошибки выделения памяти, которые обычно возникают только при большой нехватке доступной памяти. Более сложные ловушки могут отслеживать структуру выделения, анализировать использование памяти или сообщать о возникновении какой-либо определенной ситуации.

## <a name="see-also"></a>См. также

- [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)