---
title: Использование методов профилирования для сбора данных производительности из командной строки | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2117fc729ef7e7190e5f1a46fe05d0d91daf63c6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Использование методов профилирования для сбора данных о производительности из командной строки
Выбор программ командной строки и параметров средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] зависит от таких факторов, как тип профилируемого приложения, метод профилирования, который нужно использовать, а также от того, какой код (машинный или [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]) использовался для написания приложения.  
  
 В этом разделе подразделы, касающиеся процедур командной строки, упорядочены в соответствии с выбранным методом профилирования.  
  
## <a name="in-this-topic"></a>Содержание раздела  
 [Использование метода выборки для сбора статистики производительности](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Использование метода инструментирования для сбора подробных сведений о времени](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Применение методов анализа использования памяти .NET для сбора сведений о выделении памяти и времени существования объектов](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Использование метода параллелизма для сбора сведений о состязании за ресурсы и действиях потока](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Добавление данных уровневого взаимодействия в сеанс профилирования](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Использование метода выборки для сбора статистики производительности  
 Метод выборки средств профилирования позволяет собирать в сеансе профилирования данные производительности с заданными интервалами. Данные выборки позволяют получить представление о проблемах производительности, связанных с ограничением ЦП, и могут послужить хорошей отправной точкой для анализа производительности приложения.  
  
 Профилировщик можно запустить одновременно с приложением или присоединить к уже запущенному экземпляру приложения.  
  
|Задача|Тип целевого приложения|  
|----------|-----------------------------|  
|**Запуск приложения**|-   [Автономные приложения](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Присоединение к выполняемому процессу**|-   [Автономные приложения .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Автономные приложения в машинном коде](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Веб-приложения ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Службы .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Службы в машинном коде](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Использование метода инструментирования для сбора подробных сведений о времени  
 Метод инструментирования средств профилирования обеспечивает сбор данных производительности из копий двоичных файлов приложения, в которых содержатся зонды для записи сведений о производительности. Данные инструментирования собираются в начале и в конце выполнения каждой инструментированной функции и при каждом вызове других функций из этой инструментированной функции. Метод инструментирования удобно использовать для обнаружения проблем производительности, связанных с проблемами ввода-вывода, например проблемой использования диска.  
  
 Для создания инструментированного двоичного файла используется средство [VInstr.exe](../profiling/vsinstr.md). После инициализации профилировщика данные автоматически собираются из инструментированных двоичных файлов при запуске целевого приложения.  
  
 **Тип целевого приложения**  
  
-   [Автономные компоненты .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Автономные компоненты в машинном коде](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Статически скомпилированные веб-приложения ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Динамически скомпилированные веб-приложения ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler.md)  
  
-   [Службы .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Службы в машинном коде](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Применение методов анализа использования памяти .NET для сбора сведений о выделении памяти и времени существования объектов  
 Метод анализа использования памяти средств профилирования .NET позволяет собирать сведения о выделении памяти [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], а также сведения о времени существования объектов в [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Вы можете запустить целевое приложение с помощью профилировщика, присоединить профилировщик к выполняемому экземпляру приложения и создать инструментированные версии приложения для сбора подробных сведений о времени вместе с данными использования памяти [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
|Задача|Тип целевого приложения|  
|----------|-----------------------------|  
|**Запуск приложения**|-   [Автономные приложения .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Присоединение к выполняемому процессу**|-   [Автономные приложения .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Веб-приложения ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Службы .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Инструментированные модули**|-   [Автономные компоненты .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Статически скомпилированные веб-приложения ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Динамически скомпилированные веб-приложения ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Службы .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Использование метода параллелизма для сбора сведений о состязании за ресурсы и действиях потока  
 Метод параллелизма средств профилирования позволяет собирать сведения о состязании за ресурсы, а также о действиях потоков и процессов в многопоточных приложениях.  
  
 Профилировщик можно использовать при запуске приложения или присоединить к уже запущенному экземпляру приложения.  
  
|Задача|Тип целевого приложения|  
|----------|-----------------------------|  
|**Запуск приложения**|-   [Автономное приложение .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Автономное приложение в машинном коде](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Присоединение к выполняемому процессу**|-   [Автономное приложение .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Автономное приложение в машинном коде](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Веб-приложение ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Служба .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Служба в машинном коде](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Добавление данных уровневого взаимодействия в сеанс профилирования  
 Добавление данных об уровневом взаимодействии в сеанс профилирования требует определенных процедур со средствами профилирования командной строки. См. раздел [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
## <a name="see-also"></a>См. также  
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)