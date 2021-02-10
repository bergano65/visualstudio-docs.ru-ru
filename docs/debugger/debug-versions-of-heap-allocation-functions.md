---
title: Версии отладки функций выделения кучи | Документация Майкрософт
description: Используйте версии отладки функций выделения кучи в библиотеке CRT. Эти функции называются так же, как и их версии для выпуска с присоединенным _dbg.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eedf9259f7bc62f32ca563d863a7fb686b8f6f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873123"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Версии отладки функций выделения кучи
Библиотека CRT содержит специальные отладочные версии функций выделения кучи. Эти функции называются так же, как и их версии для выпуска с присоединенным к ним _dbg. В этом разделе описываются различия между версией функции CRT для окончательного выпуска и версией _dbg; для примера взяты `malloc`и `_malloc_dbg`.

 Если определен флаг [_DEBUG](/cpp/c-runtime-library/debug), CRT сопоставляет все вызовы [malloc](/cpp/c-runtime-library/reference/malloc) с [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Таким образом, чтобы получить преимущества режима отладки, не придется переписывать код и заменять `_malloc_dbg` на `malloc`.

 Конечно, при желании можно и явно вызывать `_malloc_dbg`. Явный вызов `_malloc_dbg` имеет свои преимущества:

- Отслеживание выделений типа `_CLIENT_BLOCK`.

- Запись имени исходного файла и номера строки, где был сделан запрос на выделение памяти.

  Если не нужно преобразовывать вызовы `malloc` в `_malloc_dbg`, данные исходного файла можно получить путем определения флага [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), который заставляет препроцессор непосредственно преобразовывать все вызовы `malloc` в вызовы `_malloc_dbg` вместо применения оболочки для `malloc`.

  Чтобы отследить отдельные типы выделений памяти в клиентских блоках, нужно непосредственно вызвать функцию `_malloc_dbg` и задать параметру `blockType` значение `_CLIENT_BLOCK`.

  Если _DEBUG не определен, вызовы `malloc` не задействуются, вызовы `_malloc_dbg` преобразуются в вызовы `malloc`, определение [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) игнорируется, а данные исходного файла относительно запросов на выделение не предоставляются. Поскольку `malloc`не имеет параметра типа блока, запросы на тип `_CLIENT_BLOCK` обрабатываются как стандартные выделения.

## <a name="see-also"></a>См. также

- [Методы отладки CRT](../debugger/crt-debugging-techniques.md)