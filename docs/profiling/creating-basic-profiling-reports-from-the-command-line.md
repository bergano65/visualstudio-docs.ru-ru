---
title: "Создание базовых отчетов профилирования из командной строки | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Создание базовых отчетов профилирования из командной строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе описываются основные команды VSPerfReport, которые создают отчеты со значениями, разделенными запятыми \(CSV\), из файла данных профилирования с расширением .vsp или .vsps.  Описание всех параметров отчета см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
## Команды отчета  
 Используйте одну из следующих команд, чтобы создать отчет для заданного файла профилирования данных.  
  
 **VSPerfReport** `VSPFile` **\/Summary:All**  
 Создает все отчеты, доступные для файла с расширением .vsp или .vsps.  
  
 **VSPerfReport** `VSPFile` **\/Summary:**`ReportType`\[,`ReportType`...\]  
 Создает заданные типы отчета.  
  
 **VSPerfReport** `VSPFile` **\/CallTrace**  
 Создает отчет, в котором перечисляются все события сбора данных.  Только для метода инструментирования.  
  
## Сводный отчет параметров типа  
 В следующей таблице приводится описание отчетов, которые создаются заданным параметром типа отчета.  Столбцы отчета зависят от метода профилирования, который был использован для сбора данных.  
  
|Сводный параметр|Описание отчета|Ссылка на отчет|  
|----------------------|---------------------|---------------------|  
|**CallerCallee**|Представляет отношения "родитель\-потомок" между функциями.|-   [Данные выборки](../profiling/caller-callee-view-sampling-data.md)<br />-   [Данные инструментирования](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Данные выборки памяти .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Данные инструментирования памяти .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Данные конфликтов](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Содержит перечень данных профилирования по функциям.|-   [Данные выборки](../profiling/functions-view-sampling-data.md)<br />-   [Данные инструментирования](../profiling/functions-view-instrumentation-data.md)<br />-   [Данные выборки памяти .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Данные инструментирования памяти .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Данные конфликтов](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Представляет пути исполнения и данные профилирования функций в сеансе профилирования.|-   [Данные инструментирования](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Данные выборки](../profiling/call-tree-view-sampling-data.md)<br />-   [Данные выборки памяти .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Данные инструментирования памяти .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Данные конфликтов](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|Перечисляет значения счетчика производительности Windows и метки профилирования, которые были собраны в сеансе профилирования.|-   [Представление меток](../profiling/marks-view.md)|  
|**Ip**|Перечисляет данные профилирования по инструкциям.|-   [Данные выборки](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Данные выборки памяти .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Данные конфликтов](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Перечисляет время жизни выделенных объектов.|-   [Представление "Время существования объектов"](../profiling/object-lifetime-view.md)|  
|**Line**|Перечисляет данные профилирования по строке исходного кода.|-   [Данные выборки](../profiling/lines-view-sampling-data.md)<br />-   [Данные выборки памяти .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Данные конфликтов](../profiling/lines-view-contention-data.md)|  
|**Header**|Сведения заголовка файла данных профилирования.|Зависит от файла.|  
|**Mark**|Метки профилирования, собранные в сеансе профилирования.|-   [Представление меток](../profiling/marks-view.md)|  
|**Module**|Перечисляет данные профилирования для модулей.|-   [Данные выборки](../profiling/modules-view-sampling-data.md)<br />-   [Данные инструментирования](../profiling/modules-view-instrumentation-data.md)<br />-   [Данные выборки памяти .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Данные инструментирования памяти .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Данные конфликтов](../profiling/modules-view-contention-data.md)|  
|**Process**|Перечисляет данные профилирования для процессов.|-   [Представление "Процесс"](../profiling/process-view.md)<br />-   [Данные конфликтов](../profiling/process-view-contention-data.md)|  
|**Thread**|Перечисляет данные профилирования для потоков.|-   [Представление "Процесс"](../profiling/process-view.md)|  
|**Type**|Перечисляются данные профилирования по типу.|-   [Представление выделения](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|Конфликты обращения к ресурсам.|-   [Конфликты обращения к ресурсам](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Перечисляются проблемы правил производительности.|-   Перечисляются идентификаторы CheckId и расположение исходного кода проблемы правила.|  
|**ETW**|Перечисляются события трассировки событий Windows, собранные в ходе сеанса профилирования.|-   [Отчет по трассировке событий Windows](../profiling/event-tracing-for-windows-etw-report.md)|