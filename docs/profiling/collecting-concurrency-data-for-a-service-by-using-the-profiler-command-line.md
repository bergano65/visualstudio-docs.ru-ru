---
title: 'Командная строка профилировщика: получение данных о параллелизме для службы'
description: Сбор сведений о состязании за ресурсы и действиях потока с использованием метода параллелизма в средствах профилирования Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8ae2d3678ec05ce583c9c0b7daf202f3272f4b77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868456"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Сбор данных параллелизма для службы с помощью средств командной строки профилировщика
Метод параллелизма средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] позволяет собирать данные о конфликтах ресурсов и действиях потока, показывающие использование ЦП, конфликты потоков, миграцию потоков, задержки синхронизации, области перекрывающегося ввода-вывода и другие системные события.

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. Дополнительные сведения см. в статье [Средства оценки производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Стандартные задачи

|Задача|См. также|
|----------|---------------------|
|**Присоединение к выполняющейся службе .NET**|-   [Практическое руководство. Присоединение профилировщика к службе .NET для сбора данных параллелизма](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных о взаимодействии уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Присоединение к выполняющейся службе C/C++**|-   [Практическое руководство. Присоединение профилировщика к собственной службе для сбора данных параллелизма](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Связанные задачи

### <a name="profile-windows-services"></a>Профилирование служб Windows

|Задача|См. также|
|----------|---------------------|
|**Профилирование с помощью метода выборки**|-   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Профилирование выделения памяти .NET и сбора мусора**|-   [Сбор данных об использовании памяти .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Профилирование данных параллелизма

|Задача|См. также|
|----------|---------------------|
|**Профилирование автономных приложений**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Профилирование веб-приложений ASP.NET**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Анализ представлений и отчетов данных параллелизма
- [Представления данных о конфликтах ресурсов](../profiling/resource-contention-data-views.md)

- [Визуализатор параллелизма](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Справочник
- [Справочник по средствам профилирования из командной строки](../profiling/command-line-profiling-tools-reference.md)
