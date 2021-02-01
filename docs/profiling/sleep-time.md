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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e66e62c2f7d78003581b12121844090c9754c2cc
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720063"
---
# <a name="sleep-time"></a>Время ожидания
Эти сегменты на временной шкале связаны с временем блокировки, отнесенным к категории спящего режима. Категория спящего режима подразумевает, что поток "добровольно" освободил логическое ядро и не выполняет никакой работы. В это время поток был заблокирован в интерфейсе API, который визуализатор параллелизма интерпретирует как спящий режим. К этой группе относятся такие интерфейсы API, как `Sleep()` и `SwitchToThread()`.

## <a name="see-also"></a>См. также
- [Представление "Потоки"](../profiling/threads-view-parallel-performance.md)