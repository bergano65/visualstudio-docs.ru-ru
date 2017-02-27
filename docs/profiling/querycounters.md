---
title: "Параметр QueryCounters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Параметр QueryCounters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр **QueryCounters** перечисляет доступные в компьютере счетчики производительности ЦП \(оборудования\).  
  
 Параметр **QueryCounters** должен быть единственным параметром в командной строке.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### Параметры  
 Нет  
  
## Заметки  
 При использовании метода инструментирования профилировщик может собирать значения одного или нескольких счетчиков производительности ЦП при каждом событии сбора данных.  При использовании для профилирования метода выборки можно указать одно событие счетчика и несколько случаев события, которые можно использования в качестве интервала выборки.  
  
 Различные процессоры предоставляют различные счетчики производительности ЦП.  Профилировщик определяет набор универсальных счетчиков, которые могут использоваться в большинстве процессоров.  Параметр **QueryCounters** обеспечивает перечисление как имен универсальных счетчиков, так и имен счетчиков, характерных для процессора.  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)