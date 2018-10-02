---
title: Сбор статистики по веб-приложениям ASP.NET при помощи метода выборки профилировщика из командной строки | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6573084e1db304438dd2bda1815605f36eecd691
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561183"
---
# <a name="collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line"></a>Сбор статистики по веб-приложениям ASP.NET при помощи метода выборки профилировщика из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [сбор статистики приложения для веб-приложений ASP.NET, с помощью метода выборки Profiler из командной строки](https://docs.microsoft.com/visualstudio/profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line).  
  
В этом разделе описаны процедуры и параметры для сбора статистики производительности веб-приложения ASP.NET с использованием средств командной строки **VSPerfASPNETCmd** и **VSPerfCmd** и метода профилирования выборки.  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Несмотря на то, что средство **VSPerfCmd** предоставляет полый доступ к функциональности средств профилирования, включая приостановку и возобновление профилирования, сбор дополнительных данных от процессора и счетчиков производительности Windows, следует использовать средство командной строки **VSPerfASPNETCmd**, если эта функциональность не требуется. Средство командной строки **VSPerfASPNETCmd** является предпочтительным при выполнении профилирования веб-сайтов ASP.NET с помощью отдельного профилировщика. В отличие от средства [VSPerfCmd](../profiling/vsperfcmd.md), нет необходимости устанавливать переменные среды и перезагружать компьютер. Дополнительные сведения см.в статье [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) (Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Присоединение профилировщика к приложению ASP.NET**|-   [Практическое руководство. Присоединение профилировщика к веб-приложению ASP.NET для сбора статистики приложения](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
### <a name="profiling-aspnet-web-applications"></a>Профилирование веб-приложений ASP.NET  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Профилирование выделения памяти и сбора мусора**|-   [Сбор данных об использовании памяти](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="sampling-method"></a>Способ выборки  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование автономных (клиентских) приложений**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|-   **Профилирование служб**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Анализ представлений и отчетов данных выборки  
 [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)



