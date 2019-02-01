---
title: Время ожидания | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8a79bbca9f6275f115105cc2ba6b001ac0ca7d44
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774624"
---
# <a name="sleep-time"></a>Время ожидания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эти сегменты на временной шкале связаны с временем блокировки, отнесенным к категории спящего режима. Категория спящего режима подразумевает, что поток "добровольно" освободил логическое ядро и не выполняет никакой работы. В это время поток был заблокирован в интерфейсе API, который визуализатор параллелизма интерпретирует как спящий режим. К этой группе относятся такие интерфейсы API, как `Sleep()` и `SwitchToThread()`.  
  
## <a name="see-also"></a>См. также раздел  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)
