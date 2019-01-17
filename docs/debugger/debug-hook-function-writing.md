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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9218c36f550c61484054d180ecb4dccb1ca53f3d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947508"
---
# <a name="debug-hook-function-writing"></a>Написание функций отладочных ловушек
В этом подразделе дается краткое описание нескольких функций отладочных ловушек, которые можно написать самостоятельно. Эти функции позволяют разместить пользовательский код в заранее определенных местах в контексте стандартной процедуры отладки.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Функции-ловушки клиентского блока](../debugger/client-block-hook-functions.md)  
 В разделе приводится руководство по написанию функций и заготовки функций, проверяющих или выводящих содержимое, которое хранится в блоках типа _CLIENT_BLOCK.  
  
 [Функции-ловушки выделения](../debugger/allocation-hook-functions.md)  
 В разделе приведено определение функции-ловушки выделения, описываются способы их использования, ограничения, а также примеры заготовок.  
  
 [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 В разделе рассказывается об ограничениях, связанных с функциями-ловушками выделения, которые явно пропускают блоки `_CRT_BLOCK` при вызове функций библиотеки CRT, выделяющих внутреннюю память. Также в разделе описываются последствия, которые могут возникнуть, если ловушка приложения обработает блоки `_CRT_BLOCK` (с примерами), и способы изменения стандартной функции-ловушки выделения **CrtDefaultAllocHook**.  
  
 [Отчетные функции-ловушки](../debugger/report-hook-functions.md)  
 Раздел посвящен функции `_CrtSetReportHook`, которая позволяет фильтровать отчеты, чтобы отобрать выделения конкретного типа. В этом разделе также приведена ее заготовка.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Методы отладки CRT](../debugger/crt-debugging-techniques.md)  
 Раздел содержит сведения о методах отладки библиотеки времени выполнения языка C, к которым относятся: использование библиотеки отладки CRT, макрос для отчета, различия между функциями `malloc` и `_malloc_dbg`, написание отладочных функций-ловушек, а также отладочная куча CRT.