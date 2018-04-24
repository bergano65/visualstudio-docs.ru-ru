---
title: Отчет операций диска (представление "Потоки") | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afe999ea56dbbdfd2179307f69ec12df92c612e9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="disk-operations-report-threads-view"></a>Отчет операций диска (представление потоков)
В отчете операций диска показаны дисковые операции ввода-вывода в каналах диска.  
  
 Для каждого типа доступа к диску, выполняемого от имени процесса, профилируемого в текущем периоде, выводятся следующие сведения:  
  
-   имя и идентификатор процесса, который обращался к диску;  
  
-   идентификатор потока, который обращался к диску;  
  
-   имя файла, к которому был получен доступ;  
  
-   число операций чтения на файл;  
  
-   количество считанных байтов;  
  
-   задержка чтения в миллисекундах;  
  
-   число операций записи;  
  
-   число записанных байтов;  
  
-   задержка записи в миллисекундах.  
  
## <a name="see-also"></a>См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)