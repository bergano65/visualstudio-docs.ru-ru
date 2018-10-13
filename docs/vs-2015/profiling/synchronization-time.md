---
title: Время синхронизации | Документы Майкрософт
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
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d7fe50e8b678e6baa02deeab5f111c71645dbb4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219730"
---
# <a name="synchronization-time"></a>Время синхронизации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эти сегменты на временной шкале связаны с периодами блокирования, отнесенными к категории синхронизации. Если поток помечается как заблокированный в процессе синхронизации, подразумевается одно из следующего:  
  
-   Выполнение потока могло привести к вызову известного интерфейса API синхронизации потока, например, `EnterCriticalSection()` или `WaitForSingleObject()`.  
  
-   Алгоритм сопоставления интерфейсов API не может быть полноценным, поэтому некоторые интерфейсы API, которые могли быть сопоставлены с другими категориями, могут также отображаться как синхронизация, так как кадр в стеке вызовов в итоге достиг базового примитива блокирования ядра, сопоставленного с этой категорией.  
  
 Чтобы понять исходную причину события блокировки потока, внимательно просмотрите стеки вызовов блокировки и отчеты профилей.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)



