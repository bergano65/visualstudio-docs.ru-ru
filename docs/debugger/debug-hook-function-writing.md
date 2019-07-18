---
title: Написание функций отладочных ловушек | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82145d39adc519bfd1324cc36805cea7b97b1664
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563377"
---
# <a name="debug-hook-function-writing"></a>Написание функций отладочных ловушек
В этом подразделе дается краткое описание нескольких функций отладочных ловушек, которые можно написать самостоятельно. Эти функции позволяют разместить пользовательский код в заранее определенных местах в контексте стандартной процедуры отладки.

## <a name="in-this-section"></a>В этом разделе
 [Функции-ловушки клиентского блока](../debugger/client-block-hook-functions.md) предоставляет руководство и прототип для написания функций, проверяющих или выводящих содержимое, данные, хранящиеся в блоках типа _CLIENT_BLOCK.

 [Функции-ловушки выделения](../debugger/allocation-hook-functions.md) определяет функции-ловушки выделения, способы их использования, указывает ограничения, а также приведена ее заготовка.

 [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) рассказывается об ограничениях на функции-ловушки выделения, которые явно пропускают `_CRT_BLOCK` блокирует при вызове функций библиотеки CRT, выделяющих внутреннюю память. Также в разделе описываются последствия, которые могут возникнуть, если ловушка приложения обработает блоки `_CRT_BLOCK` (с примерами), и способы изменения стандартной функции-ловушки выделения **CrtDefaultAllocHook**.

 [Функции ловушек отчетов](../debugger/report-hook-functions.md) описание `_CrtSetReportHook`, которое можно использовать для фильтрации отчеты, чтобы отобрать выделения конкретного типа. В этом разделе также приведена ее заготовка.

## <a name="related-sections"></a>Связанные разделы

- [Методы отладки CRT](../debugger/crt-debugging-techniques.md) -ссылки на методы отладки библиотеки времени выполнения C, включая использование библиотеки отладки CRT, макрос для отчета, различия между `malloc` и `_malloc_dbg`, написание отладочных функций-ловушек, а также CRT отладочной кучи.