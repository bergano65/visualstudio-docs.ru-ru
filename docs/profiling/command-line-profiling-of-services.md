---
title: Профилирование служб из командной строки | Документы Майкрософт
description: Сведения об использовании Средств профилирования из командной строки для сбора данных о производительности для служб Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dd77161184c5cb8be89ed522bbf06b6d80ca4bee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969507"
---
# <a name="command-line-profiling-of-services"></a>Профилирование служб из командной строки
В этом разделе описываются процедуры и параметры сбора данных о производительности для служб Windows с помощью средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] из командной строки.

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. Дополнительные сведения см. в статье [Средства оценки производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Стандартные задачи

| Задача | См. также |
| - | - |
| **Сбор статистики приложения.** Использование метода выборки для сбора статистики производительности. Данные выборки служат для анализа проблем использования ЦП и для изучения общих характеристик производительности приложения. | -   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Сбор подробных данных о времени.** Использование метода инструментирования для сбора подробных данных о времени. Данные инструментирования удобно использовать для анализа ошибок ввода-вывода и подробного анализа сценариев приложений. | -   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Сбор данных об использовании памяти .NET.** Использование выборки или инструментирования для сбора данных о выделения памяти .NET, содержащих размер и количество объектов, для которых выделена память. Кроме того, можно собирать данные о времени существования объектов, в которых указывается размер и количество объектов, собранных в каждом поколении сборки мусора. | -   [Сбор данных об использовании памяти .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Сбор данных о параллелизме.** Использование метода параллелизма для сбора данных о конфликтах ресурсов и действиях потока, позволяющих определить использование ЦП, конфликты потоков, миграцию потоков, задержки синхронизации, области перекрывающегося ввода-вывода и другие системные события. | -   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Добавление данных взаимодействия между уровнями.** Можно добавлять данные производительности о синхронных вызовах ADO.NET, выполняемых службой к базе данных Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. | -   [Сбор данных о взаимодействии уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Связанные задачи

|Задача|См. также|
|----------|---------------------|
|**Профилирование автономных (клиентских) приложений**|-   [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Профилирование приложений ASP.NET**|-   [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
