---
title: Отладочные версии функций выделения кучи | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0fde776e9f2bd48aca92c7ba6d7f1fe1e23f01a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738371"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Версии отладки функций выделения кучи
Библиотека CRT содержит специальные отладочные версии функций выделения кучи. Эти функции называются так же, как и их версии для выпуска с присоединенным к ним _dbg. В этом разделе описываются различия между версией функции CRT для окончательного выпуска и версией _dbg; для примера взяты `malloc`и `_malloc_dbg`.

 Если определен [_DEBUG](/cpp/c-runtime-library/debug) , CRT сопоставляет все вызовы [malloc](/cpp/c-runtime-library/reference/malloc) с [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Таким образом, чтобы получить преимущества режима отладки, не придется переписывать код и заменять `_malloc_dbg` на `malloc`.

 Конечно, при желании можно и явно вызывать `_malloc_dbg`. Явный вызов `_malloc_dbg` имеет свои преимущества:

- Отслеживание выделений типа `_CLIENT_BLOCK`.

- Запись имени исходного файла и номера строки, где был сделан запрос на выделение памяти.

  Если вы не хотите преобразовывать `malloc` вызовы в `_malloc_dbg`, можно получить сведения об исходном файле, определив [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), что заставляет препроцессор напрямую сопоставлять все вызовы `malloc` с `_malloc_dbg`, вместо того чтобы полагаться на оболочку  `malloc`.

  Чтобы отследить отдельные типы выделений памяти в клиентских блоках, нужно непосредственно вызвать функцию `_malloc_dbg` и задать параметру `blockType` значение `_CLIENT_BLOCK`.

  Если _DEBUG не определен, вызовы `malloc` не переносятся, вызовы `_malloc_dbg` разрешаются в `malloc`, определение [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) игнорируется, а сведения о файлах исходного кода, относящиеся к запросу на выделение, не предоставляются. Поскольку `malloc`не имеет параметра типа блока, запросы на тип `_CLIENT_BLOCK` обрабатываются как стандартные выделения.

## <a name="see-also"></a>См. также

- [Методы отладки CRT](../debugger/crt-debugging-techniques.md)