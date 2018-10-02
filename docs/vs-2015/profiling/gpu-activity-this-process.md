---
title: Активность GPU (этот процесс) | Документы Майкрософт
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
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc7741e46d9b7ae3bf7e53e6a07f5601e7dbbd83
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572449"
---
# <a name="gpu-activity-this-process"></a>Активность GPU (этот процесс)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [активность GPU (этот процесс)](https://docs.microsoft.com/visualstudio/profiling/gpu-activity-this-process).  
  
Сегменты **Активность GPU (этот процесс)** в представлении потоков визуализатора параллелизма представляют моменты времени, когда GPU выполнял обработку запросов от имени текущего процесса. Эти запросы отправляются в GPU как пакеты прямого доступа к памяти (DMA). Длина сегмента представляет время, в течение которого GPU выполнял обработку пакета DMA от имени текущего процесса.  
  
 При выборе сегмента активности GPU в отчете на вкладке **Текущие** отображаются сведения об обработанном пакете DMA. Эти сведения включают время ожидания пакета в очереди оборудования, связанной с ядром DirectX; процесс, отправивший пакет; и время, которое потребовалось для обработки пакета. Процесс, отличный от текущего процесса, может физически отправлять пакет DMA в графический процессор. Визуализатор параллелизма может обнаруживать отправку работы в GPU другим процессом от имени текущего процесса.



