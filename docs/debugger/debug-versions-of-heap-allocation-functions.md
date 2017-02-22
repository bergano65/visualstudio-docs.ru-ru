---
title: "Версии отладки функций выделения кучи | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC - макрос"
  - "_malloc_dbg - функция"
  - "отладка [CRT], функции-ловушки выделения"
  - "отладка утечек памяти, функции библиотеки отладки CRT"
  - "выделение кучи, отладка"
  - "malloc - функция"
  - "утечки памяти, функции библиотеки отладки CRT"
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Версии отладки функций выделения кучи
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Библиотека CRT содержит специальные отладочные версии функций выделения кучи.  Эти функции называются так же, как и их версии для выпуска с присоединенным к ним \_dbg.  В этом разделе описываются различия между версией функции CRT для окончательного выпуска и версией \_dbg; для примера взяты `malloc`и `_malloc_dbg`.  
  
 Если указано [\_DEBUG](/visual-cpp/c-runtime-library/debug), CRT преобразует все вызовы [malloc](/visual-cpp/c-runtime-library/reference/malloc) в вызовы [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg).  Таким образом, чтобы получить преимущества режима отладки, не придется переписывать код и заменять `_malloc_dbg` на `malloc`.  
  
 Конечно, при желании можно и явно вызывать `_malloc_dbg`.  Явный вызов `_malloc_dbg` имеет свои преимущества:  
  
-   Отслеживание выделений типа `_CLIENT_BLOCK`.  
  
-   Запись имени исходного файла и номера строки, где был сделан запрос на выделение памяти.  
  
 Если не нужно преобразовывать вызовы `malloc` в `_malloc_dbg`, данные исходного файла можно получить путем определения [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc), который заставляет препроцессор непосредственно преобразовывать все вызовы `malloc` в вызовы `_malloc_dbg` вместо применения оболочки для `malloc`.  
  
 Чтобы отследить отдельные типы выделений памяти в клиентских блоках, нужно непосредственно вызвать функцию `_malloc_dbg` и задать параметру `blockType` значение `_CLIENT_BLOCK`.  
  
 Если \_DEBUG не определен, вызовы `malloc` не задействуются, вызовы `_malloc_dbg` преобразуются в вызовы `malloc`, определения [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) не обрабатываются, а данные исходного файла относительно запросов на выделение не предоставляются.  Поскольку `malloc`не имеет параметра типа блока, запросы на тип `_CLIENT_BLOCK` обрабатываются как стандартные выделения.  
  
## См. также  
 [Методы отладки CRT](../debugger/crt-debugging-techniques.md)