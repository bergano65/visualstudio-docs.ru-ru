---
title: "Время синхронизации | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.synchronization
helpviewer_keywords: Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8252bc569ef17725570b5222afa12a59c387c278
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="synchronization-time"></a>Время синхронизации
Эти сегменты на временной шкале связаны с периодами блокирования, отнесенными к категории синхронизации. Если поток помечается как заблокированный в процессе синхронизации, подразумевается одно из следующего:  
  
-   Выполнение потока могло привести к вызову известного интерфейса API синхронизации потока, например, `EnterCriticalSection()` или `WaitForSingleObject()`.  
  
-   Алгоритм сопоставления интерфейсов API не может быть полноценным, поэтому некоторые интерфейсы API, которые могли быть сопоставлены с другими категориями, могут также отображаться как синхронизация, так как кадр в стеке вызовов в итоге достиг базового примитива блокирования ядра, сопоставленного с этой категорией.  
  
 Чтобы понять исходную причину события блокировки потока, внимательно просмотрите стеки вызовов блокировки и отчеты профилей.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)