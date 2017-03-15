---
title: "Время вытеснения | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8263523a1f322119ed1c251e583f0977e55d0585
ms.lasthandoff: 02/22/2017

---
# <a name="preemption-time"></a>Время вытеснения
Эти сегменты на временной шкале связаны с периодом времени блокирования, занесенным в категорию вытеснения Эта категория означает, что поток отключается по одной из следующих причин:  
  
-   Его заменил планировщик, используя поток с более высоким приоритетом.  
  
-   Квант времени выполнения потока истек; другие потоки были готовы к выполнению.  
  
 В это время поток был заблокирован по причине ожидания ядра, которое визуализатор параллелизма интерпретирует как вытеснение. Сегменты вытеснения запускаются, когда поток вытесняется из логического ядра, и заканчиваются, когда этот поток возобновляет выполнение.  
  
 Подсказка к вытесненному сегменту содержит имя процесса или потока, который вызвал это вытеснение. Но это не подразумевает, что вытесненный процесс или поток в действительности выполняются во время периода вытеснения.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)
