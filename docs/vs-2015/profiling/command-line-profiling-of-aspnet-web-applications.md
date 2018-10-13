---
title: Профилирование веб-приложений ASP.NET из командной строки | Документы Майкрософт
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
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3942744df8708ff7932dc663b1c4a55ec2dad471
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257924"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Профилирование веб-приложений ASP.NET из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описываются процедуры и параметры сбора данных о производительности для веб-приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] с помощью средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] из командной строки.  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Удобный сбор базовых данных профилирования ASP.NET.** Используйте средство **VSPerfASPNETCmd** для сбора данных по выборкам, инструментированию, памяти .NET, конфликтам и взаимодействию уровней без настройки и без перезапуска Internet Information Services (IIS), которые были необходимы при работе с **VSPerfCmd**. **Средство VSPerfASPNETCmd** не позволяет собирать дополнительные данные или контролировать сбор данных. **Примечание.** **VSPerfASPNETCmd** удобно использовать в случае, если необходим автономный профилировщик для профилирования веб-сайтов ASP.NET.|-   [Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Сбор статистики приложения.** Использование метода выборки для сбора статистики производительности. Данные выборки служат для анализа проблем использования ЦП и для изучения общих характеристик производительности приложения.|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Сбор подробных данных о времени.** Использование метода инструментирования для сбора подробных данных о времени. Данные инструментирования удобно использовать для анализа ошибок ввода-вывода и подробного анализа сценариев приложений.|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Сбор данных об использовании памяти .NET.** Использование выборки или инструментирования для сбора данных о выделения памяти .NET, содержащих размер и количество объектов, для которых выделена память. Кроме того, можно собирать данные о времени существования объектов, в которых указывается размер и количество объектов, собранных в каждом поколении сборки мусора.|-   [Сбор данных об использовании памяти](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Сбор данных параллелизма.** Использование метода параллелизма для сбора данных о конфликтах ресурсов. **Примечание.** Недоступен сбор сведений об активности потока и визуализация данных для веб-приложений.|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Добавление данных взаимодействия между уровнями.** Можно добавлять данные производительности о синхронных вызовах [!INCLUDE[vstecado](../includes/vstecado-md.md)], выполняемых веб-приложением [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] к базе данных Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование автономных (клиентских) приложений**|-   [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Профилирование служб**|-   [Профилирование служб](../profiling/command-line-profiling-of-services.md)|



