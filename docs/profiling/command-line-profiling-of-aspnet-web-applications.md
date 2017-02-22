---
title: "Профилирование веб-приложений ASP.NET из командной строки | Microsoft Docs"
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
  - "профилирование приложений ASP.NET"
  - "средства профилирования, приложения ASP.NET"
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Профилирование веб-приложений ASP.NET из командной строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе описываются процедуры и параметры сбора данных о производительности для веб\-приложений [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] с помощью средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] из командной строки.  
  
> [!NOTE]
>  Функции усиленной безопасности в Windows 8 и Windows Server 2012 требуют значительных изменений в способе сбора данных профилировщиком Visual Studio на этих платформах.  Для Приложений Магазина Windows также требуются новые методы сбора.  См. раздел [Профилирование приложений для Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Общие задачи  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Удобный сбор базовых данных профилирования ASP.NET.** Воспользуйтесь средством **VSPerfASPNETCmd** для сбора данных по выборкам, инструментированию, памяти .NET, конфликтам и взаимодействию уровней без настройки и без перезапуска Internet Information Services \(IIS\), которые были необходимы при работе с **VSPerfCmd**.  **VSPerfASPNETCmd** не позволяет собирать дополнительные данные или контролировать сбор данных. **Note:**  **VSPerfASPNETCmd** удобно использовать в случае, если необходим автономный профилировщик для профилирования веб\-сайтов ASP.NET.|-   [Быстрое профилирование веб\-сайтов с помощью средства VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Сбор статистики приложения.** Использование метода выборки для сбора статистики производительности.  Данные выборки служат для анализа проблем использования ЦП и для изучения общих характеристик производительности приложения.|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Сбор подробных данных о времени.** Использование метода инструментирования для сбора подробных данных о времени.  Данные инструментирования удобно использовать для анализа ошибок ввода\-вывода и подробного анализа сценариев приложений.|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Сбор данных об использовании памяти .NET.** Использование выборки или инструментирования для сбора данных о выделении памяти .NET, содержащих размер и количество объектов, для которых выделена память.  Кроме того, можно собирать данные о времени существования объектов, в которых указывается размер и количество объектов, собранных в каждом поколении сборки мусора.|-   [Сбор данных об использовании памяти](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Сбор данных параллелизма.** Использование метода параллелизма для сбора данных о конфликтах ресурсов. **Note:**  Недоступен сбор сведений об активности потока и визуализация данных для веб\-приложений.|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Добавление данных взаимодействия между уровнями.** Можно добавлять данные производительности о синхронных вызовах [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)], выполняемых веб\-приложением [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] к базе данных Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## Связанные задачи  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Профилирование автономных \(клиентских\) приложений**|-   [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Профилирование служб**|-   [Службы профилирования](../profiling/command-line-profiling-of-services.md)|