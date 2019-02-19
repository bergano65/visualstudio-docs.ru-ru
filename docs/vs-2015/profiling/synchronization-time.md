---
title: Время синхронизации | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 218f333f97e8252993f87893238a0f51f964d6c1
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54790338"
---
# <a name="synchronization-time"></a>Время синхронизации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эти сегменты на временной шкале связаны с периодами блокирования, отнесенными к категории синхронизации. Если поток помечается как заблокированный в процессе синхронизации, подразумевается одно из следующего:  
  
- Выполнение потока могло привести к вызову известного интерфейса API синхронизации потока, например, `EnterCriticalSection()` или `WaitForSingleObject()`.  
  
- Алгоритм сопоставления интерфейсов API не может быть полноценным, поэтому некоторые интерфейсы API, которые могли быть сопоставлены с другими категориями, могут также отображаться как синхронизация, так как кадр в стеке вызовов в итоге достиг базового примитива блокирования ядра, сопоставленного с этой категорией.  
  
  Чтобы понять исходную причину события блокировки потока, внимательно просмотрите стеки вызовов блокировки и отчеты профилей.  
  
## <a name="see-also"></a>См. также раздел  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)
