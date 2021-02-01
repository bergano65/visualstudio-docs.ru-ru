---
title: Активность GPU (подкачка) | Документы Майкрософт
description: Сведения о сегментах "Активность GPU (подкачка)" на вкладке "Потоки" визуализатора параллелизма. Сегменты представляют время, когда GPU обрабатывал запросы на подкачку.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2bdf1fcffad90155baba8f92d11e31d1b316710b
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801184"
---
# <a name="gpu-activity-paging"></a>Активность GPU (подкачка)
Сегменты **Активность GPU (подкачка)** на вкладке **Потоки** представляют время, когда GPU выполнял обработку запросов подкачки.  Длина сегмента представляет время, в течение которого GPU выполнял обработку пакета подкачки прямого доступа к памяти (DMA). Как правило, пакеты подкачки связаны с передачей памяти между ЦП и графическим процессором.

 При выборе сегмента подкачки GPU в отчете на вкладке **Текущие** отображаются сведения об обработанном пакете DMA. Эти сведения включают время ожидания пакета в очереди оборудования, связанной с ядром DirectX; процесс, отправивший пакет DMA; и время, которое потребовалось для обработки пакета.

## <a name="see-also"></a>См. также
- [Представление использования](../profiling/utilization-view.md)