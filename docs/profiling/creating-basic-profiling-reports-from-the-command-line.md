---
title: Создание базовых отчетов профилирования из командной строки | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c66829402c5002f21ec983a3946273f062a85cdf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017439"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Создание базовых отчетов профилирования из командной строки
В этой статье описываются основные команды VSPerfReport, которые создают отчеты со значениями, разделенными запятыми (*CSV*), из файла данных профилирования с расширением *VSP* или *VSPS*. Описание всех параметров отчета см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Команды отчета  
 Используйте одну из приведенных ниже команд, чтобы создать отчет для заданного файла профилирования данных.  
  
 **VSPerfReport** `VSPFile` **/Summary:All**  
 Создает все отчеты, доступные для файла с расширением *VSP* или *VSPS*.  
  
 **VSPerfReport** `VSPFile` **/Summary:**`ReportType`[,`ReportType`...]  
 Создает заданные типы отчетов.  
  
 **VSPerfReport** `VSPFile` **/CallTrace**  
 Создает отчет, в котором перечисляются все события сбора данных. Только для метода инструментирования.  
  
## <a name="summary-report-type-parameters"></a>Параметры типа сводного отчета  
 В представленной ниже таблице приводится описание отчетов, которые создаются для заданного параметра типа отчета. Столбцы отчета зависят от метода профилирования, который использовался для сбора данных.  
  
|Сводный параметр|Описание отчета|Ссылка на отчет|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|Представляет отношения "родитель-потомок" между функциями.|-   [Данные выборки](../profiling/caller-callee-view-sampling-data.md)<br />-   [Данные инструментирования](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Данные выборки памяти .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Данные инструментирования памяти .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Данные состязаний](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Содержит перечень данных профилирования по функциям.|-   [Данные выборки](../profiling/functions-view-sampling-data.md)<br />-   [Данные инструментирования](../profiling/functions-view-instrumentation-data.md)<br />-   [Данные выборки памяти .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Данные инструментирования памяти .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Данные состязаний](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Представляет пути выполнения и данные профилирования функций в сеансе профилирования.|-   [Данные инструментирования](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Данные выборки](../profiling/call-tree-view-sampling-data.md)<br />-   [Данные выборки памяти .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Данные инструментирования памяти .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Данные состязаний](../profiling/call-tree-view-contention-data.md)|  
|**Счетчик**|Перечисляет значения счетчиков производительности Windows и метки профилирования, которые были собраны за сеанс профилирования.|-   [Представление меток](../profiling/marks-view.md)|  
|**Ip**|Перечисляет данные профилирования по инструкциям.|-   [Данные выборки](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Данные выборки памяти .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Данные состязаний](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Перечисляет время жизни выделенных объектов.|-   [Представление "Время существования объектов"](../profiling/object-lifetime-view.md)|  
|**Line**|Перечисляет данные профилирования по строке исходного кода.|-   [Данные выборки](../profiling/lines-view-sampling-data.md)<br />-   [Данные выборки памяти .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Данные состязаний](../profiling/lines-view-contention-data.md)|  
|**Header**|Сведения о заголовке файла данных профилирования.|Зависит от файла.|  
|**Метка**|Метки профилирования, собранные за сеанс профилирования.|-   [Представление меток](../profiling/marks-view.md)|  
|**Модуль**|Перечисляет данные профилирования для модулей.|-   [Данные выборки](../profiling/modules-view-sampling-data.md)<br />-   [Данные инструментирования](../profiling/modules-view-instrumentation-data.md)<br />-   [Данные выборки памяти .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Данные инструментирования памяти .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Данные состязаний](../profiling/modules-view-contention-data.md)|  
|**Process**|Перечисляет данные профилирования для процессов.|-   [Представление "Процесс"](../profiling/process-view.md)<br />-   [Данные состязаний](../profiling/process-view-contention-data.md)|  
|**Поток**|Перечисляет данные профилирования для потоков.|-   [Представление "Процесс"](../profiling/process-view.md)|  
|**Type**|Перечисляет данные профилирования по типу.|-   [Представление "Выделения"](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|Состязания за ресурсы.|-   [Состязания за ресурсы](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Перечисляет проблемы правил производительности.|— Перечисляются идентификатор CheckId, описание и расположение исходного кода, в котором имеется проблема с правилом.|  
|**ETW**|Перечисляются события трассировки событий Windows, собранные в ходе сеанса профилирования.|-   [Отчет по трассировке событий Windows](../profiling/event-tracing-for-windows-etw-report.md)|