---
title: Время вытеснения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fd209f65464126650106eb4509cd3de39ad8c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198066"
---
# <a name="preemption-time"></a>Время вытеснения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эти сегменты на временной шкале связаны с периодом времени блокирования, занесенным в категорию вытеснения Эта категория означает, что поток отключается по одной из следующих причин:  
  
- Его заменил планировщик, используя поток с более высоким приоритетом.  
  
- Квант времени выполнения потока истек; другие потоки были готовы к выполнению.  
  
  В это время поток был заблокирован по причине ожидания ядра, которое визуализатор параллелизма интерпретирует как вытеснение. Сегменты вытеснения запускаются, когда поток вытесняется из логического ядра, и заканчиваются, когда этот поток возобновляет выполнение.  
  
  Подсказка к вытесненному сегменту содержит имя процесса или потока, который вызвал это вытеснение. Но это не подразумевает, что вытесненный процесс или поток в действительности выполняются во время периода вытеснения.  
  
## <a name="see-also"></a>См. также:  
 [Представление "Потоки"](../profiling/threads-view-parallel-performance.md)
