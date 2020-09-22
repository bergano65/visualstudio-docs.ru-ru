---
title: Сбор данных по использованию памяти для веб-приложений ASP.NET с помощью командной строки профилировщика | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f7c759d4c2c4760be6782a518f4cdf209e828d4
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2020
ms.locfileid: "90843406"
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Сбор данных об использовании памяти для веб-приложений ASP.NET с помощью командной строки профилировщика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описаны процедуры и параметры сбора данных по выделению памяти и времени существования объектов для веб-приложения ASP.NET с помощью программы командной строки **VSPerfCmd**.  
  
> [!NOTE]
> Программа **VSPerfCmd** предоставляет полный доступ к возможностям Средств профилирования, включая приостановку и возобновление профилирования, а также сбор дополнительных данных счетчиков производительности Windows и процессора. Если эти возможности не нужны, можно воспользоваться программой командной строки **VSPerfASPNETCmd**. В отличие от средства [VSPerfCmd](../profiling/vsperfcmd.md), нет необходимости устанавливать переменные среды и перезагружать компьютер. Дополнительные сведения см. [в статье Быстрое профилирование веб-сайтов с помощью VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Присоединение профилировщика к выполняющемуся приложению ASP.NET**|-   [Как присоединить профилировщик к веб-приложению ASP.NET для получения данных об использовании памяти](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Инструментирование статически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование статически скомпилированного приложения ASP.NET и сбор данных по использованию памяти](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Инструментирование динамически скомпилированных двоичных файлов**|-   [Руководство. Инструментирование динамически компилируемого ASP.NET приложения и получение данных об использовании памяти](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
### <a name="profiling-aspnet-web-applications"></a>Профилирование веб-приложений ASP.NET  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование с помощью метода выборки**|-   [Сбор статистики приложения с использованием выборки](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Профилирование данных об использовании памяти .NET Framework  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование автономных (клиентских) приложений**|-   [Сбор данных .NET Framework памяти](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Профилирование служб**|-   [Сбор данных об использовании памяти .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Анализ представлений и отчетов данных об использовании памяти .NET  
 [Представления данных в памяти .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Справочник  
 [Справочник по Средства профилирования командной строки](../profiling/command-line-profiling-tools-reference.md)
