---
title: "Время ввода-вывода (представление &quot;Потоки&quot;) | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 181fe2e869f88e58402f4ac01aa7fc2a0021adb4
ms.lasthandoff: 02/22/2017

---
# <a name="io-time-threads-view"></a>Время ввода-вывода (представление "Потоки")
Эти сегменты на временной шкале связаны с периодами времени блокирования, занесенными в категорию ввода-вывода. Это означает, что поток ожидает завершения операции ввода-вывода. Поток может быть заблокирован в интерфейсе API или на время ожидания ядра, связанного с вводом-выводом, которое визуализатор параллелизма интерпретирует как ввод-вывод. Такие API-интерфейсы, как `CreateFile()`, `ReadFile()`, и `WSARecv()`, попадают в эту группу.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)
