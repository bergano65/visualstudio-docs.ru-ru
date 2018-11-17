---
title: Параметр QueryCounters | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f5bedfd794dc7666240b1657cbdc4125b46708b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809288"
---
# <a name="querycounters"></a>Параметр QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр **QueryCounters** перечисляет доступные на компьютере счетчики производительности ЦП (оборудования).  
  
 Параметр **QueryCounters** должен быть единственным параметром в командной строке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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



