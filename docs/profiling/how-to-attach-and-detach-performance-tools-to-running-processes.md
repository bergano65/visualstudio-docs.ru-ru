---
title: "Практическое руководство. Подключение средств оценки производительности к выполняющимся процессам и отключение от этих процессов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e847e1295e4514f8e1c327f207a6ae7166c892df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Практическое руководство. Подключение средств оценки производительности к выполняющимся процессам и отключение от этих процессов
Профилировщик можно использовать для подключения к или отключения от выполняющегося процесса, чтобы упростить выборку и сбор данных производительности. Этот метод можно использовать для профилирования процесса, если необходимо запретить сбор данных о времени загрузки приложения или отследить производительность процесса после достижения им определенного состояния.  
  
> [!NOTE]
>  Следующая процедура применима к подключению и отключению процессов из интегрированной среды разработки (IDE) [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Сведения об использовании средств командной строки см. в разделе [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md). Сведения о профилировании служб см. в разделе [Профилирование служб](../profiling/command-line-profiling-of-services.md).  
  
 Процессы, доступные для профилирования, зависят от разрешений на доступ пользователя, заданных администратором компьютера. Учетная запись пользователя, например, имеет разрешения на следующее:  
  
-   расширенные возможности профилирования, если администратор задал драйвер и запускаемую службу;  
  
-   только профилирование выборки (пользователи домена);  
  
-   запрет доступа к профилированию для всех пользователей.  
  
 Дополнительные сведения см. в разделе [Профилирование и безопасность Windows Vista](../profiling/profiling-and-windows-vista-security.md) и в описании параметров ADMIN раздела [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Присоединение к выполняющемуся процессу  
  
1.  В меню **Отладка** наведите указатель мыши на **Профилировщик**, затем на **Обозреватель производительности** и выберите действие **Присоединить**.    
  
     Откроется диалоговое окно **Присоединить профилировщик к процессу**.  
  
2.  Щелкните имя процесса, к которому необходимо подключиться.  
  
3.  Нажмите кнопку **Присоединить**.  
  
### <a name="to-detach-from-a-running-process"></a>Отключение от выполняемого процесса  
  
1.  В меню **Отладка** наведите указатель мыши на **Профилировщик**, затем на **Обозреватель производительности** и выберите действие **Отсоединить**. 
  
     Откроется диалоговое окно **Присоединить профилировщик к процессу**.  
  
2.  Щелкните имя процесса, который необходимо отключить.  
  
3.  Щелкните **Отсоединить**.  
  
## <a name="see-also"></a>См. также  
 [Управление сбором данных](../profiling/controlling-data-collection.md)   
 [Общие сведения о сеансе анализа производительности](../profiling/performance-session-overview.md)   
 [Практическое руководство. Начало и окончания сбора данных о производительности](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Профилирование и безопасность Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)