---
title: Профилирование служб из командной строки | Документы Майкрософт
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
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc44d7f9ea822dfb7c5d68e6769e36a0ff9aeae4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561257"
---
# <a name="command-line-profiling-of-services"></a>Профилирование служб из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [профилирования командной строки служб Services](https://docs.microsoft.com/visualstudio/profiling/command-line-profiling-of-services).  
  
В этом разделе описываются процедуры и параметры сбора данных о производительности для служб Windows с помощью средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] из командной строки.  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Сбор статистики приложения.** Использование метода выборки для сбора статистики производительности. Данные выборки служат для анализа проблем использования ЦП и для изучения общих характеристик производительности приложения.|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Сбор подробных данных о времени.** Использование метода инструментирования для сбора подробных данных о времени. Данные инструментирования удобно использовать для анализа ошибок ввода-вывода и подробного анализа сценариев приложений.|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Сбор данных об использовании памяти .NET.** Использование выборки или инструментирования для сбора данных о выделения памяти .NET, содержащих размер и количество объектов, для которых выделена память. Кроме того, можно собирать данные о времени существования объектов, в которых указывается размер и количество объектов, собранных в каждом поколении сборки мусора.|-   [Сбор данных об использовании памяти .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Сбор данных о параллелизме.** Использование метода параллелизма для сбора данных о конфликтах ресурсов и действиях потока, позволяющих определить использование ЦП, конфликты потоков, миграцию потоков, задержки синхронизации, области перекрывающегося ввода-вывода и другие системные события.|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**Добавление данных взаимодействия между уровнями.** Можно добавлять данные производительности о синхронных вызовах ADO.NET, выполняемых службой к базе данных Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование автономных (клиентских) приложений**|-   [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Профилирование приложений ASP.NET**|-   [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|



