---
title: "Активность GPU (другие процессы) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuother"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Активность GPU (другие процессы)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Сегменты **Активности GPU \(Другие Процессы\)** в представлении потоков визуализатора параллелизма представляют моменты времени, когда GPU выполнял обработку запросов от имени других процессов в системе.  Эти запросы отправляются GPU как пакеты прямого доступа к памяти \(DMA\).  Длина сегмента представляет период времени, за который пакет был обработан GPU.  
  
 При выборе этого типа сегмента, отчет на вкладке **Текущий** отображает сведения о пакете, который был обработан.  Эти сведения включают время, которое пакет ожидал в аппаратной очереди, связанной с обработчиком DirectX, процесс, отправивший пакет, и время, необходимое для обработки пакета.