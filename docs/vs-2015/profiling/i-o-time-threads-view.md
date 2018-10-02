---
title: Время ввода-вывода (представление "Потоки") | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25512da43fc32b42c2a1f79e3c8dbe992ea30ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572545"
---
# <a name="io-time-threads-view"></a>Время ввода-вывода (представление "Потоки")
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ввод вывод времени (представление "Потоки")](https://docs.microsoft.com/visualstudio/profiling/i-o-time-threads-view).  
  
Эти сегменты на временной шкале связаны с периодами времени блокирования, занесенными в категорию ввода-вывода. Это означает, что поток ожидает завершения операции ввода-вывода. Поток может быть заблокирован в интерфейсе API или на время ожидания ядра, связанного с вводом-выводом, которое визуализатор параллелизма интерпретирует как ввод-вывод. Такие API-интерфейсы, как `CreateFile()`, `ReadFile()`, и `WSARecv()`, попадают в эту группу.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)



