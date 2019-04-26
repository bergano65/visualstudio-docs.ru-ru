---
title: Время синхронизации | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae73f7b9a9838a006dce47bf44b0ed46aa0b84fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965314"
---
# <a name="synchronization-time"></a>Время синхронизации
Эти сегменты на временной шкале связаны с периодами блокирования, отнесенными к категории синхронизации. Если поток помечается как заблокированный в процессе синхронизации, подразумевается одно из следующего:

- Выполнение потока могло привести к вызову известного интерфейса API синхронизации потока, например, `EnterCriticalSection()` или `WaitForSingleObject()`.

- Алгоритм сопоставления интерфейсов API не может быть полноценным, поэтому некоторые интерфейсы API, которые могли быть сопоставлены с другими категориями, могут также отображаться как синхронизация, так как кадр в стеке вызовов в итоге достиг базового примитива блокирования ядра, сопоставленного с этой категорией.

  Чтобы понять исходную причину события блокировки потока, внимательно просмотрите стеки вызовов блокировки и отчеты профилей.

## <a name="see-also"></a>См. также
- [Представление "Потоки"](../profiling/threads-view-parallel-performance.md)