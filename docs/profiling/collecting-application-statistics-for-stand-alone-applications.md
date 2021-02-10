---
title: 'Командная строка профилировщика: сбор статистики по автономным приложениям'
description: Сбор статистики по автономным приложениям с помощью командной строки профилировщика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 053f846b15968ad7a5714f99779944bd63a8b6d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868391"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Сбор статистики по автономным приложениям с помощью командной строки профилировщика
В этом разделе описываются процедуры и параметры для сбора статистики о производительности клиентского (автономного) приложения с использованием метода выборки в командной строке.

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. Дополнительные сведения см. в статье [Средства оценки производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Стандартные задачи

|Задача|См. также|
|----------|---------------------|
|**Запуск приложения с использованием профилировщика**|-   [Практическое руководство. Запуск автономного приложения и сбор статистики приложения](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Присоединение профилировщика к выполняющемуся приложению .NET Framework**|-   [Практическое руководство. Присоединение профилировщика к приложению .NET Framework для сбора статистики приложения](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Присоединение профилировщика к выполняющемуся приложению C/C++**|-   [Практическое руководство. Присоединение профилировщика к собственному приложению и сбор статистики приложения](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>Связанные задачи

### <a name="profile-stand-alone-applications"></a>Профилирование автономных приложений

|Задача|См. также|
|----------|---------------------|
|**Инструментирование приложения**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Сбор данных о выделении памяти .NET и сборке мусора**|-   [Сбор данных об использовании памяти .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Сбор данных о конфликтах ресурсов и выполнении потоков**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Профилирование с помощью метода выборки

|Задача|См. также|
|----------|---------------------|
|**Профилирование веб-приложений ASP.NET**|-   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Профилирование служб**|-   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) Содержит описание сбора статистики о производительности служб Windows с помощью метода выборки.|

### <a name="analyze-sampling-data-views-and-reports"></a>Анализ представлений и отчетов данных выборки
- [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)
