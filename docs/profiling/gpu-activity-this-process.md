---
title: "Активность GPU (этот процесс) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 255a1ff62d4f9c444169e1330dcd11eb8e1030ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-this-process"></a>Активность GPU (этот процесс)
Сегменты **Активность GPU (этот процесс)** в представлении потоков визуализатора параллелизма представляют моменты времени, когда GPU выполнял обработку запросов от имени текущего процесса. Эти запросы отправляются в GPU как пакеты прямого доступа к памяти (DMA). Длина сегмента представляет время, в течение которого GPU выполнял обработку пакета DMA от имени текущего процесса.  
  
 При выборе сегмента активности GPU в отчете на вкладке **Текущие** отображаются сведения об обработанном пакете DMA. Эти сведения включают время ожидания пакета в очереди оборудования, связанной с ядром DirectX; процесс, отправивший пакет; и время, которое потребовалось для обработки пакета. Процесс, отличный от текущего процесса, может физически отправлять пакет DMA в графический процессор. Визуализатор параллелизма может обнаруживать отправку работы в GPU другим процессом от имени текущего процесса.