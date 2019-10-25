---
title: Определить, повреждают ли указатели адрес памяти | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8313bc8e0419e281dceefbafd6dcdcc2f368580f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734246"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Как определить, повреждают ли указатели адрес памяти?
## <a name="problem-description"></a>Описание проблемы
 Возможно, один из указателей повреждает память по адресу 0x00408000. Как определить, что происходит в этой точке?

## <a name="solution"></a>Решение

#### <a name="check-for-heap-corruption"></a>Проверка целостности кучи

- В большинстве случаев повреждение памяти происходит из-за повреждения кучи. Используйте программу глобальных флагов (gflags.exe) или pageheap.exe. См. раздел [http://support.microsoft.com/default.aspx?scid=kb; en-US; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Поиск места изменения адреса памяти

1. Задайте точку останова данных по адресу 0x00408000. Подробнее см. раздел [Установка точки останова, действующей при изменении данных (только для машинного кода C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. При попадании в точку останова используйте окно **Память** для просмотра содержимого памяти начиная с адреса 0x00408000. Дополнительные сведения см. в разделе [окна памяти](../debugger/memory-windows.md).

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)