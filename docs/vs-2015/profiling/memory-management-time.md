---
title: Время управления памятью | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9371c4d5249539c80299fd1b1573eba19c9dd14f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558115"
---
# <a name="memory-management-time"></a>Время управления памятью
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [время управления памятью](https://docs.microsoft.com/visualstudio/profiling/memory-management-time).  
  
Эти сегменты на временной шкале связаны с периодами времени блокирования, занесенными в категорию управления памятью. Это означает, что поток блокируется событием, связанным с операцией по управлению памятью, например разбиением по страницам. В это время поток был заблокирован в интерфейсе API либо состоянии ядра, которое визуализатор параллелизма интерпретирует как управление памятью. К этим событиям относятся, например, разбиение по страницам и выделение памяти.  
  
 Проанализируйте соответствующие стеки вызова и отчеты профилирования, чтобы лучше разобраться с основными причинами блокировок, которые относятся к категории управления памятью.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)



