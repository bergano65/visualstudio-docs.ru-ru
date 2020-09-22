---
title: Сбор статистики по автономным приложениям с помощью командной строки профилировщика | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03e27d021b8b3c5ec29a8646a1bbe7bc6ebdecc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843008"
---
# <a name="collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Сбор статистики по автономным приложениям с помощью командной строки профилировщика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описываются процедуры и параметры для сбора статистики о производительности клиентского (автономного) приложения с использованием метода выборки в командной строке.  
  
> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Запуск приложения с использованием профилировщика**|-   [Руководство. Запуск автономного приложения и сбор статистики приложения](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Присоединение профилировщика к выполняющемуся приложению .NET Framework**|-   [Как присоединить профилировщик к .NET Framework приложению и выполнить сбор статистики приложения](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Присоединение профилировщика к выполняющемуся приложению C/C++**|-   [Как присоединить профилировщик к собственному приложению и выполнить сбор статистики приложения](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных об уровневом взаимодействии](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
### <a name="profiling-stand-alone-applications"></a>Профилирование автономных приложений  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Инструментирование приложения**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Сбор данных о выделении памяти .NET и сборке мусора**|-   [Сбор данных .NET Framework памяти](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Сбор данных о конфликтах ресурсов и выполнении потоков**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Профилирование с помощью метода выборки  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Профилирование веб-приложений ASP.NET**|-   [Сбор статистики приложения с использованием выборки](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
|**Профилирование служб**|-   [Сбор статистики приложения с использованием выборки](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Содержит описание сбора статистики о производительности служб Windows с помощью метода выборки.|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Анализ представлений и отчетов данных выборки  
 [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)
