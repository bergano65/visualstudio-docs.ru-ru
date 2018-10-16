---
title: Время вытеснения | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ac7152ec663a0a7b7bbbeee5c30a38885623cb9
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254763"
---
# <a name="preemption-time"></a>Время вытеснения
Эти сегменты на временной шкале связаны с периодом времени блокирования, занесенным в категорию вытеснения Эта категория означает, что поток отключается по одной из следующих причин:  
  
-   Его заменил планировщик, используя поток с более высоким приоритетом.  
  
-   Квант времени выполнения потока истек; другие потоки были готовы к выполнению.  
  
 В это время поток был заблокирован по причине ожидания ядра, которое визуализатор параллелизма интерпретирует как вытеснение. Сегменты вытеснения запускаются, когда поток вытесняется из логического ядра, и заканчиваются, когда этот поток возобновляет выполнение.  
  
 Подсказка к вытесненному сегменту содержит имя процесса или потока, который вызвал это вытеснение. Но это не подразумевает, что вытесненный процесс или поток в действительности выполняются во время периода вытеснения.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)