---
title: Активность GPU (подкачка) | Документы Майкрософт
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
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 015fa34d2bb87cf98a64fb3431a6440202cf729b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195862"
---
# <a name="gpu-activity-paging"></a>Активность GPU (подкачка)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Сегменты **Активность GPU (подкачка)** на вкладке "Потоки" представляют время, когда GPU выполнял обработку запросов подкачки.  Длина сегмента представляет время, в течение которого GPU выполнял обработку пакета подкачки прямого доступа к памяти (DMA). Как правило, пакеты подкачки связаны с передачей памяти между ЦП и графическим процессором.  
  
 При выборе сегмента подкачки GPU в отчете на вкладке **Текущие** отображаются сведения об обработанном пакете DMA. Эти сведения включают время ожидания пакета в очереди оборудования, связанной с ядром DirectX; процесс, отправивший пакет DMA; и время, которое потребовалось для обработки пакета.  
  
## <a name="see-also"></a>См. также  
 [Представление использования](../profiling/utilization-view.md)



