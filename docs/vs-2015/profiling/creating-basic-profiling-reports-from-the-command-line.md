---
title: Создание базовых отчетов профилирования из командной строки | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f13921dea810ab2185e626cc2889f339d9d174f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537193"
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Создание базовых отчетов профилирования из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описываются основные команды VSPerfReport, которые создают отчеты со значениями, разделенными запятыми (CSV), из файла данных профилирования с расширением VSP или VSPS. Описание всех параметров отчета см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Команды отчета  
 Используйте одну из приведенных ниже команд, чтобы создать отчет для заданного файла профилирования данных.  
  
 **VSPerfReport** `VSPFile` **/Summary:All**  
 Создает все отчеты, доступные для файла с расширением VSP или VSPS.  
  
 **VSPerfReport** `VSPFile` **/Summary:** `ReportType` [,`ReportType`...]  
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
|**См**|Перечисляет данные профилирования по инструкциям.|-   [Данные выборки](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Данные выборки памяти .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Данные состязаний](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Перечисляет время жизни выделенных объектов.|-   [Представление "время существования объекта"](../profiling/object-lifetime-view.md)|  
|**Линия**|Перечисляет данные профилирования по строке исходного кода.|-   [Данные выборки](../profiling/lines-view-sampling-data.md)<br />-   [Данные выборки памяти .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Данные состязаний](../profiling/lines-view-contention-data.md)|  
|**Верхняя часть**|Сведения о заголовке файла данных профилирования.|Зависит от файла.|  
|**Метка**|Метки профилирования, собранные за сеанс профилирования.|-   [Представление меток](../profiling/marks-view.md)|  
|**Модуль**|Перечисляет данные профилирования для модулей.|-   [Данные выборки](../profiling/modules-view-sampling-data.md)<br />-   [Данные инструментирования](../profiling/modules-view-instrumentation-data.md)<br />-   [Данные выборки памяти .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Данные инструментирования памяти .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Данные состязаний](../profiling/modules-view-contention-data.md)|  
|**Процесс**|Перечисляет данные профилирования для процессов.|-   [Представление процессов](../profiling/process-view.md)<br />-   [Данные состязаний](../profiling/process-view-contention-data.md)|  
|**Поток**|Перечисляет данные профилирования для потоков.|-   [Представление процессов](../profiling/process-view.md)|  
|**Тип**|Перечисляет данные профилирования по типу.|-   [Представление "выделения"](../profiling/dotnet-memory-allocations-view.md)|  
|**Состязания**|Состязания за ресурсы.|-   [Состязание за ресурсы](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Перечисляет проблемы правил производительности.|— Перечисляются идентификатор CheckId, описание и расположение исходного кода, в котором имеется проблема с правилом.|  
|**Трассировка событий Windows**|Перечисляются события трассировки событий Windows, собранные в ходе сеанса профилирования.|-   [Отчет по трассировке событий Windows](../profiling/event-tracing-for-windows-etw-report.md)|
