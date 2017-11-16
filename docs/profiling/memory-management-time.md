---
title: "Время управления памятью | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.paging
helpviewer_keywords: Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c04bdfd537a57bc4578b122d45b6b86eedc6e603
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="memory-management-time"></a>Время управления памятью
Эти сегменты на временной шкале связаны с периодами времени блокирования, занесенными в категорию управления памятью. Это означает, что поток блокируется событием, связанным с операцией по управлению памятью, например разбиением по страницам. В это время поток был заблокирован в интерфейсе API либо состоянии ядра, которое визуализатор параллелизма интерпретирует как управление памятью. К этим событиям относятся, например, разбиение по страницам и выделение памяти.  
  
 Проанализируйте соответствующие стеки вызова и отчеты профилирования, чтобы лучше разобраться с основными причинами блокировок, которые относятся к категории управления памятью.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)