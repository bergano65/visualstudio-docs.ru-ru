---
title: Сбор статистики приложения для служб с помощью метода выборки профилировщика | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a847777ad3d5b12162eedc8e998098ad20926a1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295559"
---
# <a name="collecting-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Сбор статистики приложения для служб с помощью метода выборки профилировщика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описываются процедуры и параметры сбора статистики о производительности для служб Windows с помощью метода выборки из командной строки.  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Присоединение профилировщика к службе .NET**|-   [Практическое руководство. Присоединение профилировщика к службе .NET для сбора статистики приложения](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Присоединение профилировщика к службе C/C++**|-   [Практическое руководство. Присоединение профилировщика к собственной службе для сбора статистики приложения](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
### <a name="profiling-windows-services"></a>Профилирование служб Windows  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Профилирование выделения памяти .NET и сбора мусора**|-   [Сбор данных об использовании памяти .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Профилирование с помощью метода выборки  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование автономных (клиентских) приложений**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Профилирование веб-приложений ASP.NET**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Анализ представлений и отчетов данных выборки  
 [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)



