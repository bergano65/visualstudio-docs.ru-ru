---
title: Активность GPU (подкачка) | Документы Майкрософт
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
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c11bd0fd8f348ff90e95660e5df03a4aa591d96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559223"
---
# <a name="gpu-activity-paging"></a>Активность GPU (подкачка)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [активность GPU (подкачка)](https://docs.microsoft.com/visualstudio/profiling/gpu-activity-paging).  
  
Сегменты **Активность GPU (подкачка)** на вкладке "Потоки" представляют время, когда GPU выполнял обработку запросов подкачки.  Длина сегмента представляет время, в течение которого GPU выполнял обработку пакета подкачки прямого доступа к памяти (DMA). Как правило, пакеты подкачки связаны с передачей памяти между ЦП и графическим процессором.  
  
 При выборе сегмента подкачки GPU в отчете на вкладке **Текущие** отображаются сведения об обработанном пакете DMA. Эти сведения включают время ожидания пакета в очереди оборудования, связанной с ядром DirectX; процесс, отправивший пакет DMA; и время, которое потребовалось для обработки пакета.  
  
## <a name="see-also"></a>См. также  
 [Представление использования](../profiling/utilization-view.md)



