---
title: Использование методов профилирования из командной строки для получения данных о производительности
description: Сведения о том, что выбор программ командной строки и параметров средств профилирования Visual Studio зависит от таких факторов, как тип профилируемого приложения.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ebcd3fdbc09029309d1b06efc75417add223ce04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917593"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Использование методов профилирования для сбора данных о производительности из командной строки
Выбор программ командной строки и параметров Средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] зависит от таких факторов, как тип профилируемого приложения, метод профилирования, который нужно использовать, а также от того, какой код (машинный или .NET Framework) использовался для написания приложения.

 В этом разделе подразделы, касающиеся процедур командной строки, упорядочены в соответствии с выбранным методом профилирования.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Использование метода выборки для сбора статистики производительности
 Метод выборки средств профилирования позволяет собирать в сеансе профилирования данные производительности с заданными интервалами. Данные выборки позволяют получить представление о проблемах производительности, связанных с ограничением ЦП, и могут послужить хорошей отправной точкой для анализа производительности приложения.

 Профилировщик можно запустить одновременно с приложением или присоединить к уже запущенному экземпляру приложения.

|Задача|Тип целевого приложения|
|----------|-----------------------------|
|**Запуск приложения**|-   [Автономные приложения](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Присоединение к выполняемому процессу**|-   [Автономные приложения .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Автономные приложения в машинном коде](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [Веб-приложения ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Службы .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Службы в машинном коде](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Использование метода инструментирования для сбора подробных сведений о времени
 Метод инструментирования средств профилирования обеспечивает сбор данных производительности из копий двоичных файлов приложения, в которых содержатся зонды для записи сведений о производительности. Данные инструментирования собираются в начале и в конце выполнения каждой инструментированной функции и при каждом вызове других функций из этой инструментированной функции. Метод инструментирования удобно использовать для обнаружения проблем производительности, связанных с проблемами ввода-вывода, например проблемой использования диска.

 Для создания инструментированного двоичного файла используется средство [VInstr.exe](../profiling/vsinstr.md). После инициализации профилировщика данные автоматически собираются из инструментированных двоичных файлов при запуске целевого приложения.

 **Тип целевого приложения**

- [Автономные компоненты .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Автономные компоненты в машинном коде](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Статически скомпилированные веб-приложения ASP.NET](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Динамически скомпилированные веб-приложения ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [Службы .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Службы в машинном коде](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Применение методов анализа использования памяти .NET для сбора сведений о выделении памяти и времени существования объектов
 Метод анализа использования памяти Средств профилирования .NET позволяет собирать сведения о выделении памяти .NET Framework, а также сведения о времени существования объектов в .NET Framework.

 Вы можете запустить целевое приложение с помощью профилировщика, присоединить профилировщик к выполняемому экземпляру приложения и создать инструментированные версии приложения для сбора подробных сведений о времени вместе с данными использования памяти .NET Framework.

|Задача|Тип целевого приложения|
|----------|-----------------------------|
|**Запуск приложения**|-   [Автономные приложения .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Присоединение к выполняемому процессу**|-   [Автономные приложения .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [Веб-приложения ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Службы .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Инструментированные модули**|-   [Автономные компоненты .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Статически скомпилированные веб-приложения ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Динамически скомпилированные веб-приложения ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Службы .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Использование метода параллелизма для сбора сведений о состязании за ресурсы и действиях потока
 Метод параллелизма средств профилирования позволяет собирать сведения о состязании за ресурсы, а также о действиях потоков и процессов в многопоточных приложениях.

 Профилировщик можно использовать при запуске приложения или присоединить к уже запущенному экземпляру приложения.

|Задача|Тип целевого приложения|
|----------|-----------------------------|
|**Запуск приложения**|-   [Автономное приложение .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Автономное приложение в машинном коде](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Присоединение к выполняемому процессу**|-   [Автономное приложение .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Автономное приложение в машинном коде](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [Веб-приложение ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Служба .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Служба в машинном коде](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Добавление данных уровневого взаимодействия в сеанс профилирования
 Добавление данных об уровневом взаимодействии в сеанс профилирования требует определенных процедур со средствами профилирования командной строки. См. [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>См. также
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
