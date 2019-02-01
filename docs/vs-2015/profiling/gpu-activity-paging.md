---
title: Активность GPU (подкачка) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5979ccf8cafedb849b7ae9f7af6b0b35096e624f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769100"
---
# <a name="gpu-activity-paging"></a>Активность GPU (подкачка)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Сегменты **Активность GPU (подкачка)** на вкладке "Потоки" представляют время, когда GPU выполнял обработку запросов подкачки.  Длина сегмента представляет время, в течение которого GPU выполнял обработку пакета подкачки прямого доступа к памяти (DMA). Как правило, пакеты подкачки связаны с передачей памяти между ЦП и графическим процессором.  
  
 При выборе сегмента подкачки GPU в отчете на вкладке **Текущие** отображаются сведения об обработанном пакете DMA. Эти сведения включают время ожидания пакета в очереди оборудования, связанной с ядром DirectX; процесс, отправивший пакет DMA; и время, которое потребовалось для обработки пакета.  
  
## <a name="see-also"></a>См. также раздел  
 [Представление использования](../profiling/utilization-view.md)
