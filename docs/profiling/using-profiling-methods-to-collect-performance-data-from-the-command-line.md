---
title: "Использование методов профилирования для сбора данных о производительности из командной строки | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Использование методов профилирования для сбора данных о производительности из командной строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Выбор программ командной строки средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и параметров зависит от таких факторов, как тип профилируемого приложения, метод профилирования, который нужно использовать, а также от того, какой код, машинный или [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], использовался для написания приложения.  
  
 В этом разделе разделы, касающиеся процедур, упорядочены в соответствии с выбранным методом профилирования.  
  
## В этом разделе  
 [Использование метода выборки для сбора статистики производительности](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Использование метода инструментирования для сбора подробных данных о времени](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Применение методов анализа использования памяти .NET для сбора данных о выделении памяти и времени существования объектов](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Использование метода параллелизма для сбора данных о конфликтах ресурсов и действиях потока](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Добавление данных об уровневом взаимодействии в сеанс профилирования](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Использование метода выборки для сбора статистики производительности  
 Метод выборки средств профилирования позволяет собирать в сеансе профилирования данные о производительности с заданными интервалами.  Данные выборки позволяют получить общее представление о проблемах граничной производительности ЦП и могут послужить хорошей отправной точкой для анализа производительности приложения.  
  
 Профилировщик можно запустить одновременно с приложением или присоединить к уже запущенному экземпляру приложения.  
  
|Задача|Тип целевого приложения|  
|------------|-----------------------------|  
|**Запуск приложения**|-   [Автономные приложения](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Присоединение к выполняемому процессу**|-   [Автономные приложения .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Собственные автономные приложения](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Application%20Statistics%20by%20Using%20the%20Command%20Line.md)<br />-   [Веб\-приложения ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Службы .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Собственные службы](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Использование метода инструментирования для сбора подробных данных о времени  
 Метод инструментирования средств профилирования обеспечивает сбор данных о производительности из копий двоичных файлов приложения, в которых содержатся зонды для записи сведений о производительности.  Данные инструментирования собираются в начале и в конце выполнения каждой инструментированной функции и при каждом вызове других функций из этой инструментированной функции.  Метод инструментирования удобно использовать для обнаружения проблем производительности, связанных с проблемами ввода\-вывода, например проблемой использования диска.  
  
 Для создания инструментированного двоичного файла используется средство [VInstr.exe](../profiling/vsinstr.md).  После инициализации профилировщика данные автоматически собираются из инструментированных двоичных файлов при запуске целевого приложения.  
  
 **Тип целевого приложения**  
  
-   [Автономные компоненты .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Собственные автономные компоненты](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Статически скомпилированные веб\-приложения ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Динамически скомпилированные веб\-приложения ASP.NET](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)  
  
-   [Службы .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Собственные службы](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Применение методов анализа использования памяти .NET для сбора данных о выделении памяти и времени существования объектов  
 Метод анализа использования памяти средств профилирования .NET [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] позволяет собирать данные о выделении памяти [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], а также сведения о времени существования объектов в .  
  
 Можно запустить целевое приложение с использованием профилировщика, присоединить профилировщик к выполняемому экземпляру приложения и создать инструментированные версии приложения для сбора подробных сведений о времени вместе с данными об использовании памяти [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
|Задача|Тип целевого приложения|  
|------------|-----------------------------|  
|**Запуск приложения**|-   [Автономные приложения .NET Framework](../Topic/How%20to:%20Launch%20a%20Stand-Alone%20.NET%20Framework%20Application%20with%20the%20Profiler%20to%20Collect%20Memory%20Data%20by%20Using%20the%20Command%20Line.md)|  
|**Присоединение к выполняемому процессу**|-   [Автономные приложения .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Веб\-приложения ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Службы .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Инструментированные модули**|-   [Автономные компоненты .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Статически скомпилированные веб\-приложения ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Динамически скомпилированные веб\-приложения ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Службы .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Использование метода параллелизма для сбора данных о конфликтах ресурсов и действиях потока  
 Метод параллелизма средств профилирования позволяет собирать данные о конфликтах ресурсов, а также действиях потоков и процессов в многопоточных приложениях.  
  
 Профилировщик можно использовать при запуске приложения или присоединить к уже запущенному экземпляру приложения.  
  
|Задача|Тип целевого приложения|  
|------------|-----------------------------|  
|**Запуск приложения**|-   [Автономное приложение .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Автономное собственное приложение](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Присоединение к выполняемому процессу**|-   [Автономное приложение .NET Framework](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20.NET%20Framework%20Stand-Alone%20Application%20to%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [Собственное автономное приложение](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [Веб\-приложение ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Служба .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Собственная служба](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Добавление данных об уровневом взаимодействии в сеанс профилирования  
 Добавление данных об уровневом взаимодействии в сеанс профилирования требует определенных процедур со средствами профилирования командной строки.  См. раздел [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
## См. также  
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)