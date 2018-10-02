---
title: Отчет операций диска (представление "Потоки") | Документы Майкрософт
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
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe16116131c1ed6d0233abbd2e0480946b5a5423
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560648"
---
# <a name="disk-operations-report-threads-view"></a>Отчет операций диска (представление потоков)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [отчет операций диска (представление "Потоки")](https://docs.microsoft.com/visualstudio/profiling/disk-operations-report-threads-view).  
  
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



