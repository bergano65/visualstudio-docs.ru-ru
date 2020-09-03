---
title: Представление "Процесс" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0436401c458a7d6771a2785028a8b5fe0ef57546
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180210"
---
# <a name="process-view"></a>Представление "Процесс"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В представлении процесса отображаются данные о профилировании для процессов и потоков, которые выполнялись во время сеанса профилирования.  
  
 Процессы упорядочены по имени. Потоки указываются как дочерние узлы создавших их процессов. Потоки именуются по запустивших их функциям или по метке **[ntdll.dll]** при отсутствии доступных символов.  
  
 Чтобы добавить или удалить столбцы, щелкните правой кнопкой мыши в представлении и выберите **Добавить или удалить столбцы**. Кроме того, щелкнув имя столбца, можно сортировать данные. Дополнительные сведения см. в статье [How to: Customize Report View Columns](../profiling/how-to-customize-report-view-columns.md) (Практическое руководство. Настройка столбцов представлений отчета).  
  
 Столбцы в представлении процесса являются одинаковыми для данных, которые созданы с помощью методов выборки и инструментирования, а также для данных, которые включают данные памяти .NET. В следующей таблице описаны значения столбцов.  
  
|Столбец|Description|  
|------------|-----------------|  
|**Уникальный идентификатор**|Созданный профилировщиком идентификатор, уникальным образом определяющий процесс или поток.|  
|**Идентификатор**|Созданный системой идентификатор процесса или потока.|  
|**Название**|Имя процесса или потока.|  
|**Время начала**|Количество миллисекунд или циклов процессора от начала профилирования до запуска процесса или потока.|  
|**Время окончания**|Количество миллисекунд или циклов процессора от начала профилирования до завершения процесса или потока.|  
  
## <a name="see-also"></a>См. также:  
 [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)   
 [Представления данных метода инструментирования](../profiling/instrumentation-method-data-views.md)   
 [Представления данных в памяти .NET](../profiling/dotnet-memory-data-views.md)
