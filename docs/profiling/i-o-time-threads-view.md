---
title: Время ввода-вывода (представление "Потоки") | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5743062a56dbf5afac76698d4ca9247d5652833
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997472"
---
# <a name="io-time-threads-view"></a>время ввода-вывода (представление "Потоки")
Эти сегменты на временной шкале связаны с периодами времени блокирования, занесенными в категорию ввода-вывода. Это означает, что поток ожидает завершения операции ввода-вывода. Поток может быть заблокирован в интерфейсе API или на время ожидания ядра, связанного с вводом-выводом, которое визуализатор параллелизма интерпретирует как ввод-вывод. Такие API-интерфейсы, как `CreateFile()`, `ReadFile()`, и `WSARecv()`, попадают в эту группу.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)