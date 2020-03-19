---
title: Активность GPU (другие процессы) | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a502590c20fce1455d9259ae681178d9cd48e33
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969506"
---
# <a name="gpu-activity-other-processes"></a>Активность GPU (другие процессы)
Сегменты **Активность GPU (другие процессы)** в представлении потоков визуализатора параллелизма представляют моменты времени, когда GPU выполнял обработку запросов от имени других процессов в системе. Эти запросы отправляются в GPU как пакеты прямого доступа к памяти (DMA).  Длина сегмента представляет количество времени, затраченного на обработку пакета графическим процессором.

 При выборе такого типа сегмента в отчете на вкладке **Текущие** отображаются сведения об обработанном пакете.  Эти сведения включают время ожидания пакета в очереди оборудования, связанной с ядром DirectX; процесс, отправивший пакет; и время, которое потребовалось для обработки пакета.