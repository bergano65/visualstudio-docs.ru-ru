---
title: Время управления памятью | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e16378663dd07bb9810661ad50d3f1c011dfdd80
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000373"
---
# <a name="memory-management-time"></a>Время управления памятью
Эти сегменты на временной шкале связаны с периодами времени блокирования, занесенными в категорию управления памятью. Это означает, что поток блокируется событием, связанным с операцией по управлению памятью, например разбиением по страницам. В это время поток был заблокирован в интерфейсе API либо состоянии ядра, которое визуализатор параллелизма интерпретирует как управление памятью. К этим событиям относятся, например, разбиение по страницам и выделение памяти.  
  
 Проанализируйте соответствующие стеки вызова и отчеты профилирования, чтобы лучше разобраться с основными причинами блокировок, которые относятся к категории управления памятью.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)