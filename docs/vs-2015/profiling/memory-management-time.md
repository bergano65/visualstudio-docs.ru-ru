---
title: Время управления памятью | Документы Майкрософт
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
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3fc38abb47c70949b63b44958e96e3b168589fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729420"
---
# <a name="memory-management-time"></a>Время управления памятью
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эти сегменты на временной шкале связаны с периодами времени блокирования, занесенными в категорию управления памятью. Это означает, что поток блокируется событием, связанным с операцией по управлению памятью, например разбиением по страницам. В это время поток был заблокирован в интерфейсе API либо состоянии ядра, которое визуализатор параллелизма интерпретирует как управление памятью. К этим событиям относятся, например, разбиение по страницам и выделение памяти.  
  
 Проанализируйте соответствующие стеки вызова и отчеты профилирования, чтобы лучше разобраться с основными причинами блокировок, которые относятся к категории управления памятью.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)



