---
title: VSPerfCmd — получение данных о времени для веб-приложения ASP.NET с помощью метода инструментирования
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 55f682152731391bdb0d4c0de0a307c00c16e2c7
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331849"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Сбор подробных данных о времени для веб-приложения ASP.NET с использованием метода инструментирования профилировщика из командной строки
В этом разделе описываются процедуры и параметры для сбора подробных данных по производительности веб-приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] с использованием программы командной строки **VSPerfCmd** и метода инструментирования.

> [!NOTE]
> Программа **VSPerfCmd** предоставляет полный доступ к возможностям Средств профилирования, включая приостановку и возобновление профилирования, а также сбор дополнительных данных счетчиков производительности Windows и процессора. Если эти возможности не нужны, можно воспользоваться программой командной строки **VSPerfASPNETCmd**. В отличие от программы командной строки [VSPerfCmd](../profiling/vsperfcmd.md), она не требует задания переменных среды и перезагрузки компьютера. Дополнительные сведения см.в статье [Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Типичные задачи

|Задача|Связанное содержимое|
|----------|---------------------|
|**Профилирование статически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование статически скомпилированного приложения ASP.NET и сбор подробных данных о времени](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Профилирование динамически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование динамически скомпилированного приложения ASP.NET и сбор подробных данных о времени](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Связанные задачи

### <a name="profile-aspnet-web-applications"></a>Профилирование веб-приложений ASP.NET

|Задача|Связанное содержимое|
|----------|---------------------|
|**Профилирование с помощью метода выборки**|-   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Профилирование выделения памяти и сбора мусора**|-   [Сбор данных об использовании памяти](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Профилирование с помощью метода инструментирования

|Задача|Связанное содержимое|
|----------|---------------------|
|**Профилирование автономных (клиентских) приложений**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Профилирование служб**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Анализ данных инструментирования представлений и отчетов
- [Представления данных метода инструментирования](../profiling/instrumentation-method-data-views.md)
