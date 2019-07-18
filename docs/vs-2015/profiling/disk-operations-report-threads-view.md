---
title: Отчет операций диска (представление "Потоки") | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: daace3e78cca67fd9b44144cd6c8a5608dbd9a1e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111198"
---
# <a name="disk-operations-report-threads-view"></a>Отчет операций диска (представление потоков)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В отчете операций диска показаны дисковые операции ввода-вывода в каналах диска.  
  
 Для каждого типа доступа к диску, выполняемого от имени процесса, профилируемого в текущем периоде, выводятся следующие сведения:  
  
- имя и идентификатор процесса, который обращался к диску;  
  
- идентификатор потока, который обращался к диску;  
  
- имя файла, к которому был получен доступ;  
  
- число операций чтения на файл;  
  
- количество считанных байтов;  
  
- задержка чтения в миллисекундах;  
  
- число операций записи;  
  
- число записанных байтов;  
  
- задержка записи в миллисекундах.  
  
## <a name="see-also"></a>См. также раздел  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)
