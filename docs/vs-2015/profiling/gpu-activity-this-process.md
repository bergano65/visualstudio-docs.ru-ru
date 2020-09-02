---
title: Активность GPU (этот процесс) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b616e307b3c42b09662be3fdad290ea9f740637c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434154"
---
# <a name="gpu-activity-this-process"></a>Активность GPU (этот процесс)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Сегменты **Активность GPU (этот процесс)** в представлении потоков визуализатора параллелизма представляют моменты времени, когда GPU выполнял обработку запросов от имени текущего процесса. Эти запросы отправляются в GPU как пакеты прямого доступа к памяти (DMA). Длина сегмента представляет время, в течение которого GPU выполнял обработку пакета DMA от имени текущего процесса.  
  
 При выборе сегмента активности GPU в отчете на вкладке **Текущие** отображаются сведения об обработанном пакете DMA. Эти сведения включают время ожидания пакета в очереди оборудования, связанной с ядром DirectX; процесс, отправивший пакет; и время, которое потребовалось для обработки пакета. Процесс, отличный от текущего процесса, может физически отправлять пакет DMA в графический процессор. Визуализатор параллелизма может обнаруживать отправку работы в GPU другим процессом от имени текущего процесса.
