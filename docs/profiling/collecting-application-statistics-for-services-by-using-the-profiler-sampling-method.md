---
title: Сбор статистики для служб Windows — метод выборки профилировщика
description: Сведения о процедурах и параметрах сбора статистики о производительности для служб Windows с использованием метода выборки из командной строки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ffbc26cb10d80aedb36d33826f9eab675957c8ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868404"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Сбор статистики приложения для служб с помощью метода выборки профилировщика
В этом разделе описываются процедуры и параметры сбора статистики о производительности для служб Windows с помощью метода выборки из командной строки.

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. См. статью [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Стандартные задачи

|Задача|См. также|
|----------|---------------------|
|**Присоединение профилировщика к службе .NET**|-   [Практическое руководство. Присоединение профилировщика к службе .NET для сбора статистики приложения](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных о взаимодействии уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Присоединение профилировщика к службе C/C++**|-   [Практическое руководство. Присоединение профилировщика к собственной службе для сбора статистики приложения](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Связанные задачи

### <a name="profile-windows-services"></a>Профилирование служб Windows

|Задача|См. также|
|----------|---------------------|
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Профилирование выделения памяти .NET и сбора мусора**|-   [Сбор данных об использовании памяти .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Профилирование с помощью метода выборки

|Задача|См. также|
|----------|---------------------|
|**Профилирование автономных (клиентских) приложений**|-   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Профилирование веб-приложений ASP.NET**|-   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Анализ представлений и отчетов данных выборки
- [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)
