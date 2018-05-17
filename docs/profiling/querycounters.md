---
title: Параметр QueryCounters | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce82016b16eef3bd7c48cb156c705d0f1b28198b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2018
---
# <a name="querycounters"></a>Параметр QueryCounters
Параметр **QueryCounters** перечисляет доступные на компьютере счетчики производительности ЦП (оборудования).  
  
 Параметр **QueryCounters** должен быть единственным параметром в командной строке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cmd  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет  
  
## <a name="remarks"></a>Примечания  
 При использовании метода инструментирования профилировщик может собирать значения одного или нескольких счетчиков производительности ЦП при каждом событии сбора данных. При использовании для профилирования метода выборки можно указать одно событие счетчика и количество его наступлений, которое будет использоваться в качестве интервала выборки.  
  
 Различные процессоры предоставляют различные счетчики производительности ЦП. Профилировщик определяет набор универсальных счетчиков, которые могут использоваться в большинстве процессоров. Параметр **QueryCounters** обеспечивает перечисление как имен универсальных счетчиков, так и имен счетчиков, характерных для процессора.  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)