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
ms.openlocfilehash: 9d7ba29383ddddc02160967a90b56046128d2f19
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62995445"
---
# <a name="io-time-threads-view"></a>время ввода-вывода (представление "Потоки")
Эти сегменты на временной шкале связаны с периодами времени блокирования, занесенными в категорию ввода-вывода. Это означает, что поток ожидает завершения операции ввода-вывода. Поток может быть заблокирован в интерфейсе API или на время ожидания ядра, связанного с вводом-выводом, которое визуализатор параллелизма интерпретирует как ввод-вывод. Такие API-интерфейсы, как `CreateFile()`, `ReadFile()`, и `WSARecv()`, попадают в эту группу.

## <a name="see-also"></a>См. также
- [Представление потоков](../profiling/threads-view-parallel-performance.md)