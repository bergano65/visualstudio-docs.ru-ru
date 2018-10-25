---
title: Время вытеснения | Документация Майкрософт
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
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f302dff3ea72217c6325aca667aec8ff4d7f218f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905237"
---
# <a name="preemption-time"></a>Время вытеснения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эти сегменты на временной шкале связаны с периодом времени блокирования, занесенным в категорию вытеснения Эта категория означает, что поток отключается по одной из следующих причин:  
  
- Его заменил планировщик, используя поток с более высоким приоритетом.  
  
- Квант времени выполнения потока истек; другие потоки были готовы к выполнению.  
  
  В это время поток был заблокирован по причине ожидания ядра, которое визуализатор параллелизма интерпретирует как вытеснение. Сегменты вытеснения запускаются, когда поток вытесняется из логического ядра, и заканчиваются, когда этот поток возобновляет выполнение.  
  
  Подсказка к вытесненному сегменту содержит имя процесса или потока, который вызвал это вытеснение. Но это не подразумевает, что вытесненный процесс или поток в действительности выполняются во время периода вытеснения.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)



