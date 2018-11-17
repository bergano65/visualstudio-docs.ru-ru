---
title: Сбор подробных сведений о времени для веб-приложения ASP.NET с использованием метода инструментирования профилировщика из командной строки | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 191d61fd14bef7b64f7095461df0cc83cdda7246
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726276"
---
# <a name="collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Сбор подробных данных о времени для веб-приложения ASP.NET с использованием метода инструментирования профилировщика из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описываются процедуры и параметры для сбора подробных данных по производительности веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] с использованием программы командной строки **VSPerfCmd** и метода инструментирования.  
  
> [!NOTE]
>  Программа **VSPerfCmd** предоставляет полный доступ к возможностям Средств профилирования, включая приостановку и возобновление профилирования, а также сбор дополнительных данных счетчиков производительности Windows и процессора. Если эти возможности не нужны, можно воспользоваться программой командной строки **VSPerfASPNETCmd**. В отличие от программы командной строки [VSPerfCmd](../profiling/vsperfcmd.md), она не требует задания переменных среды и перезагрузки компьютера. Дополнительные сведения см.в статье [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) (Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование статически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование статически скомпилированного приложения ASP.NET и сбор подробных данных о времени](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Профилирование динамически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование динамически скомпилированного приложения ASP.NET и сбор подробных данных о времени](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
### <a name="profiling-aspnet-web-applications"></a>Профилирование веб-приложений ASP.NET  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование с помощью метода выборки**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Профилирование выделения памяти и сбора мусора**|-   [Сбор данных об использовании памяти](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-instrumentation-method"></a>Профилирование с помощью метода инструментирования  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование автономных (клиентских) приложений**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Профилирование служб**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### <a name="analyzing-instrumentation-data-views-and-reports"></a>Анализ данных инструментирования представлений и отчетов  
 [Представление данных метода инструментирования](../profiling/instrumentation-method-data-views.md)



