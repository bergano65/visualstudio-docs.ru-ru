---
title: Использование командной строки Profiler для получения данных о параллелизме службы
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fba5c02846fa13cb0929a63e4007acb7db58535
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66262979"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Сбор данных параллелизма для службы с помощью средств командной строки профилировщика
Метод параллелизма средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] позволяет собирать данные о конфликтах ресурсов и действиях потока, показывающие использование ЦП, конфликты потоков, миграцию потоков, задержки синхронизации, области перекрывающегося ввода-вывода и другие системные события.

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. Дополнительные сведения см. в статье [Средства оценки производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Типичные задачи

|Задача|Связанное содержимое|
|----------|---------------------|
|**Присоединение к выполняющейся службе .NET**|-   [Практическое руководство. Присоединение профилировщика к службе .NET для сбора данных параллелизма](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных о взаимодействии уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Присоединение к выполняющейся службе C/C++**|-   [Практическое руководство. Присоединение профилировщика к собственной службе для сбора данных параллелизма](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Связанные задачи

### <a name="profile-windows-services"></a>Профилирование служб Windows

|Задача|Связанное содержимое|
|----------|---------------------|
|**Профилирование с помощью метода выборки**|-   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Профилирование выделения памяти .NET и сбора мусора**|-   [Сбор данных об использовании памяти .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Профилирование данных параллелизма

|Задача|Связанное содержимое|
|----------|---------------------|
|**Профилирование автономных приложений**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Профилирование веб-приложений ASP.NET**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Анализ представлений и отчетов данных параллелизма
- [Представления данных о конфликтах ресурсов](../profiling/resource-contention-data-views.md)

- [Визуализатор параллелизма](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Ссылка
- [Справочник по средствам профилирования из командной строки](../profiling/command-line-profiling-tools-reference.md)