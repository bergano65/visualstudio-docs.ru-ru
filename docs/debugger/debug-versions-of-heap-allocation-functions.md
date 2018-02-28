---
title: "Отладочные версии функций выделения кучи | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 63642402f6e98e42b2d4954a6065f61fb61159b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Версии отладки функций выделения кучи
Библиотека CRT содержит специальные отладочные версии функций выделения кучи. Эти функции называются так же, как и их версии для выпуска с присоединенным к ним _dbg. В этом разделе описываются различия между версией функции CRT для окончательного выпуска и версией _dbg; для примера взяты `malloc`и `_malloc_dbg`.  
  
 При [_DEBUG](/cpp/c-runtime-library/debug) будет определено, CRT преобразует все [malloc](/cpp/c-runtime-library/reference/malloc) вызовы [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Таким образом, чтобы получить преимущества режима отладки, не придется переписывать код и заменять `_malloc_dbg` на `malloc`.  
  
 Конечно, при желании можно и явно вызывать `_malloc_dbg`. Явный вызов `_malloc_dbg` имеет свои преимущества:  
  
-   Отслеживание выделений типа `_CLIENT_BLOCK`.  
  
-   Запись имени исходного файла и номера строки, где был сделан запрос на выделение памяти.  
  
 Если вы не хотите преобразовать вашей `malloc` вызовы `_malloc_dbg`, данные исходного файла можно получить путем определения [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), которое вызывает препроцессор непосредственно преобразовывать все вызовы `malloc` для `_malloc_dbg` вместо оболочка `malloc`.  
  
 Чтобы отследить отдельные типы выделений памяти в клиентских блоках, нужно непосредственно вызвать функцию `_malloc_dbg` и задать параметру `blockType` значение `_CLIENT_BLOCK`.  
  
 Если _DEBUG не определен, вызовы `malloc` не задействуются, вызовы `_malloc_dbg` можно использовать для `malloc`, определение [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) учитывается, а данные файла относительно источника запрос на выделение не предоставляется. Поскольку `malloc`не имеет параметра типа блока, запросы на тип `_CLIENT_BLOCK` обрабатываются как стандартные выделения.  
  
## <a name="see-also"></a>См. также  
 [Методы отладки CRT](../debugger/crt-debugging-techniques.md)