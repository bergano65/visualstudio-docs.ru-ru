---
title: Параметр QueryCounters | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9a4e3c9f80ed437eb4476833776c5c19689c69a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866924"
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