---
title: Время ожидания | Документы Майкрософт
description: Сведения о категории спящего режима, которая подразумевает, что поток "добровольно" освободил логическое ядро и не выполняет никакой работы.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a433d11c2684a4a39660759f33d49bd719c2b2ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960173"
---
# <a name="sleep-time"></a>Время ожидания
Эти сегменты на временной шкале связаны с временем блокировки, отнесенным к категории спящего режима. Категория спящего режима подразумевает, что поток "добровольно" освободил логическое ядро и не выполняет никакой работы. В это время поток был заблокирован в интерфейсе API, который визуализатор параллелизма интерпретирует как спящий режим. К этой группе относятся такие интерфейсы API, как `Sleep()` и `SwitchToThread()`.

## <a name="see-also"></a>См. также
- [Представление "Потоки"](../profiling/threads-view-parallel-performance.md)