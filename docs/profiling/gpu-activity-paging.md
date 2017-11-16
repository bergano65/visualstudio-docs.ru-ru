---
title: "Активность GPU (подкачка) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 960ea3a50a5c937b93b81c56e3b775d3fde49bd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-paging"></a>Активность GPU (подкачка)
Сегменты **Активность GPU (подкачка)** на вкладке "Потоки" представляют время, когда GPU выполнял обработку запросов подкачки.  Длина сегмента представляет время, в течение которого GPU выполнял обработку пакета подкачки прямого доступа к памяти (DMA). Как правило, пакеты подкачки связаны с передачей памяти между ЦП и графическим процессором.  
  
 При выборе сегмента подкачки GPU в отчете на вкладке **Текущие** отображаются сведения об обработанном пакете DMA. Эти сведения включают время ожидания пакета в очереди оборудования, связанной с ядром DirectX; процесс, отправивший пакет DMA; и время, которое потребовалось для обработки пакета.  
  
## <a name="see-also"></a>См. также  
 [Представление использования](../profiling/utilization-view.md)