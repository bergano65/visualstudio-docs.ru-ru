---
title: Отладочные версии функций выделения кучи | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 13f8d8b79ecf586048aacf3cd9442c596f184be3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691157"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Версии отладки функций выделения кучи
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Библиотека CRT содержит специальные отладочные версии функций выделения кучи. Эти функции называются так же, как и их версии для выпуска с присоединенным к ним _dbg. В этом разделе описываются различия между версией функции CRT для окончательного выпуска и версией _dbg; для примера взяты `malloc`и `_malloc_dbg`.  
  
 Когда [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) будет определен, CRT преобразует все [malloc](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) вызовы [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Таким образом, чтобы получить преимущества режима отладки, не придется переписывать код и заменять `_malloc_dbg` на `malloc`.  
  
 Конечно, при желании можно и явно вызывать `_malloc_dbg`. Явный вызов `_malloc_dbg` имеет свои преимущества:  
  
- Отслеживание выделений типа `_CLIENT_BLOCK`.  
  
- Запись имени исходного файла и номера строки, где был сделан запрос на выделение памяти.  
  
  Если вы не хотите преобразовать вашей `malloc` вызовы `_malloc_dbg`, данные исходного файла можно получить путем определения [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), который заставляет препроцессор непосредственно преобразовывать все вызовы `malloc` для `_malloc_dbg` вместо того чтобы оболочку вокруг `malloc`.  
  
  Чтобы отследить отдельные типы выделений памяти в клиентских блоках, нужно непосредственно вызвать функцию `_malloc_dbg` и задать параметру `blockType` значение `_CLIENT_BLOCK`.  
  
  Если _DEBUG не определен, вызовы `malloc` не задействуются, вызовы функций `_malloc_dbg` можно использовать для `malloc`, определение [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) игнорируется и исходные сведения о файле, относящиеся к запрос на выделение не предоставляется. Поскольку `malloc`не имеет параметра типа блока, запросы на тип `_CLIENT_BLOCK` обрабатываются как стандартные выделения.  
  
## <a name="see-also"></a>См. также  
 [Методы отладки CRT](../debugger/crt-debugging-techniques.md)
