---
title: Сбор данных о времени для ASP.NET с помощью метода инструментирования
description: Узнайте, как использовать средство VSPerfCmd для сбора подробных данных о производительности для веб-приложения ASP.NET. Оно предоставляет полный доступ к функциональным возможностям Средств профилирования.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: c0eca3aa29795da4a2d1233f0cba1774641fc364
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868326"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Сбор подробных данных о времени для веб-приложения ASP.NET с использованием метода инструментирования профилировщика из командной строки
В этом разделе описываются процедуры и параметры для сбора подробных данных по производительности веб-приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] с использованием программы командной строки **VSPerfCmd** и метода инструментирования.

> [!NOTE]
> Программа **VSPerfCmd** предоставляет полный доступ к возможностям Средств профилирования, включая приостановку и возобновление профилирования, а также сбор дополнительных данных счетчиков производительности Windows и процессора. Если эти возможности не нужны, можно воспользоваться программой командной строки **VSPerfASPNETCmd**. В отличие от программы командной строки [VSPerfCmd](../profiling/vsperfcmd.md), она не требует задания переменных среды и перезагрузки компьютера. Дополнительные сведения см.в статье [Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Стандартные задачи

|Задача|Связанное содержимое|
|----------|---------------------|
|**Профилирование статически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование статически скомпилированного приложения ASP.NET и сбор подробных данных о времени](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Профилирование динамически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование динамически скомпилированного приложения ASP.NET и сбор подробных данных о времени](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Связанные задачи

### <a name="profile-aspnet-web-applications"></a>Профилирование веб-приложений ASP.NET

|Задача|См. также|
|----------|---------------------|
|**Профилирование с помощью метода выборки**|-   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Профилирование выделения памяти и сбора мусора**|-   [Сбор данных об использовании памяти](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Профилирование с помощью метода инструментирования

|Задача|См. также|
|----------|---------------------|
|**Профилирование автономных (клиентских) приложений**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Профилирование служб**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Анализ данных инструментирования представлений и отчетов
- [Представления данных метода инструментирования](../profiling/instrumentation-method-data-views.md)
