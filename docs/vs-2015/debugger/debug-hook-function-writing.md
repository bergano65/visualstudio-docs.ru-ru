---
title: Написание функций отладочных ловушек | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47cd3d42639785290f26d7acbbad15cd948b4f51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735529"
---
# <a name="debug-hook-function-writing"></a>Написание функций отладочных ловушек
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом подразделе дается краткое описание нескольких функций отладочных ловушек, которые можно написать самостоятельно. Эти функции позволяют разместить пользовательский код в заранее определенных местах в контексте стандартной процедуры отладки.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Функции-ловушки клиентского блока](../debugger/client-block-hook-functions.md)  
 В разделе приводится руководство по написанию функций и заготовки функций, проверяющих или выводящих содержимое, которое хранится в блоках типа _CLIENT_BLOCK.  
  
 [Функции-ловушки выделения](../debugger/allocation-hook-functions.md)  
 В разделе приведено определение функции-ловушки выделения, описываются способы их использования, ограничения, а также примеры заготовок.  
  
 [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 В разделе рассказывается об ограничениях, связанных с функциями-ловушками выделения, которые явно пропускают блоки `_CRT_BLOCK` при вызове функций библиотеки CRT, выделяющих внутреннюю память. В этом разделе также описываются последствия, если ловушка выделения `_CRT_BLOCK` блоки (с примерами) и способ изменения распределения по умолчанию функция-ловушка **CrtDefaultAllocHook**.  
  
 [Отчетные функции-ловушки](../debugger/report-hook-functions.md)  
 Раздел посвящен функции `_CrtSetReportHook`, которая позволяет фильтровать отчеты, чтобы отобрать выделения конкретного типа. В этом разделе также приведена ее заготовка.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Методы отладки CRT](../debugger/crt-debugging-techniques.md)  
 Раздел содержит сведения о методах отладки библиотеки времени выполнения языка C, к которым относятся: использование библиотеки отладки CRT, макрос для отчета, различия между функциями `malloc` и `_malloc_dbg`, написание отладочных функций-ловушек, а также отладочная куча CRT.



