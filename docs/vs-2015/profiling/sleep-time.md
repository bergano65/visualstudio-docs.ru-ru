---
title: Время ожидания | Документы Майкрософт
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
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f9b86ea0fa1b7880893e4d7300efbe51a029ce7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801801"
---
# <a name="sleep-time"></a>Время ожидания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эти сегменты на временной шкале связаны с временем блокировки, отнесенным к категории спящего режима. Категория спящего режима подразумевает, что поток "добровольно" освободил логическое ядро и не выполняет никакой работы. В это время поток был заблокирован в интерфейсе API, который визуализатор параллелизма интерпретирует как спящий режим. К этой группе относятся такие интерфейсы API, как `Sleep()` и `SwitchToThread()`.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)



