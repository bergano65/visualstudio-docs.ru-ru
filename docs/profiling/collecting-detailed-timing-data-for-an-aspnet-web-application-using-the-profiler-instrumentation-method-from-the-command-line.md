---
title: "Сбор подробных данных о времени для веб-приложения ASP.NET с использованием метода инструментирования профилировщика из командной строки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "метод профилирования инструментирования"
  - "средства профилирования, метод инструментирования"
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Сбор подробных данных о времени для веб-приложения ASP.NET с использованием метода инструментирования профилировщика из командной строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе описаны процедуры и параметры для сбора подробных данных о производительности веб\-приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] с использованием метода инструментирования и средства командной строки **VSPerfCmd**.  
  
> [!NOTE]
>  Средство **VSPerfCmd** предоставляет полный доступ к функциональности средств профилирования, включая остановку и возобновление профилирования и сбор дополнительных сведений счетчиков производительности Windows и процессора.  Можно также воспользоваться средством командной строки **VSPerfASPNETCmd**, если эта функциональность не нужна.  В отличие от средства командной строки [VSPerfCmd](../profiling/vsperfcmd.md), нет необходимости устанавливать переменные окружения и перезагружать компьютер.  Для получения дополнительной информации см. [Быстрое профилирование веб\-сайтов с помощью средства VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Общие задачи  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Профилирование статически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование статически скомпилированного приложения ASP.NET и сбор подробных данных о времени](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Профилирование динамически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование динамически скомпилированного приложения ASP.NET и сбор подробных данных о времени](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)|  
  
## Связанные задачи  
  
### Профилирование веб\-приложений ASP.NET  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Профилирование с помощью метода выборки**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Профилирование выделения памяти и сбора мусора**|-   [Сбор данных об использовании памяти](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Профилирование с помощью метода инструментирования  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Профилирование автономных \(клиентских\) приложений**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Профилирование служб**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### Анализ представлений и отчетов данных инструментирования  
 [Представление данных метода инструментирования](../profiling/instrumentation-method-data-views.md)