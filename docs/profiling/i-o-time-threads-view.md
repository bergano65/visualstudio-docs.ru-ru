---
title: Время ввода-вывода (представление "Потоки") | Документация Майкрософт
description: Сведения о том, как сегменты времени ввода-вывода связаны с периодами времени блокировки, занесенными в категорию ввода-вывода, что означает, что поток ожидает завершения операции ввода-вывода.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e147d97616f846339dc12e3941f6944f277d8318
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906855"
---
# <a name="io-time-threads-view"></a>время ввода-вывода (представление "Потоки")
Эти сегменты на временной шкале связаны с периодами времени блокирования, занесенными в категорию ввода-вывода. Это означает, что поток ожидает завершения операции ввода-вывода. Поток может быть заблокирован в интерфейсе API или на время ожидания ядра, связанного с вводом-выводом, которое визуализатор параллелизма интерпретирует как ввод-вывод. Такие API-интерфейсы, как `CreateFile()`, `ReadFile()`, и `WSARecv()`, попадают в эту группу.

## <a name="see-also"></a>См. также
- [Представление потоков](../profiling/threads-view-parallel-performance.md)