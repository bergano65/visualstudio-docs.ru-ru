---
title: Присоединение средств производительности к выполняющемуся процессу
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4c4ae54d6b90166de31c338a5e606eaf31ecd6cc
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779172"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Практическое руководство. Присоединение средств производительности к выполняющемуся процессу и его отсоединение от этого процесса
Профилировщик можно использовать для подключения к или отключения от выполняющегося процесса, чтобы упростить выборку и сбор данных производительности. Этот метод можно использовать для профилирования процесса, если необходимо запретить сбор данных о времени загрузки приложения или отследить производительность процесса после достижения им определенного состояния.

> [!NOTE]
> Следующая процедура применима к подключению и отключению процессов из интегрированной среды разработки (IDE) [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Сведения об использовании инструментов командной строки см. в разделе [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md). Сведения о профилировании служб см. в разделе [Профилирование служб](../profiling/command-line-profiling-of-services.md).

 Процессы, доступные для профилирования, зависят от разрешений на доступ пользователя, заданных администратором компьютера. Учетная запись пользователя, например, имеет разрешения на следующее:

- расширенные возможности профилирования, если администратор задал драйвер и запускаемую службу;

- только профилирование выборки (пользователи домена);

- запрет доступа к профилированию для всех пользователей.

  Дополнительные сведения см. в разделе [Профилирование и безопасность Windows Vista](../profiling/profiling-and-windows-vista-security.md) и в описании параметров ADMIN раздела [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-attach-to-a-running-process"></a>Присоединение к выполняющемуся процессу

1. В меню **Отладка** наведите указатель мыши на **Профилировщик**, затем на **Обозреватель производительности** и выберите действие **Присоединить**.

     Откроется диалоговое окно **Присоединить профилировщик к процессу**.

2. Щелкните имя процесса, к которому необходимо подключиться.

3. Нажмите кнопку **Присоединить**.

### <a name="to-detach-from-a-running-process"></a>Отключение от выполняемого процесса

1. В меню **Отладка** наведите указатель мыши на **Профилировщик**, затем на **Обозреватель производительности** и выберите действие **Отсоединить**.

     Откроется диалоговое окно **Присоединить профилировщик к процессу**.

2. Щелкните имя процесса, который необходимо отключить.

3. Щелкните **Отсоединить**.

## <a name="see-also"></a>См. также
- [Управление сбором данных](../profiling/controlling-data-collection.md)
- [Общие сведения о сеансе анализа производительности](../profiling/performance-session-overview.md)
- [Практическое руководство. Начало и окончание сбора данных о производительности](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Профилирование и безопасность Windows Vista](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
