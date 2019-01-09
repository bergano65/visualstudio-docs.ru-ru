---
title: Отчет операций диска (представление "Потоки") | Документы Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 95173f260ce8ed40c607c7026df727267dd3866e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955270"
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