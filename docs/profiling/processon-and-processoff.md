---
title: "Подкоманды ProcessOn и ProcessOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Подкоманды ProcessOn и ProcessOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Подкоманды **ProcessOff** и **ProcessOn** программы VSPerfCmd.exe приостанавливают и возобновляют профилирование заданного процесса в сеансе профилирования из командной строки.  **ProcessOff** останавливает профилирование процесса, а **ProcessOn** запускает профилирование процесса.  
  
 В большинстве случаев параметр **ProcessOn** или **ProcessOff** можно задать как единственный параметр командной строки программы VSPerfCmd.exe либо в сочетании с подкомандами **GlobalOn**, **GlobalOff**, **ThreadOn** и **ThreadOff**.  
  
 Подкоманды **ProcessOn** и **ProcessOff** также взаимодействуют с подкомандами **GlobalOn** и **GlobalOff**, которые обеспечивают управление сбором данных для всех процессов сеанса профилирования с использованием командной строки, и с подкомандами **ThreadOn** и **ThreadOff**, которые позволяют управлять сбором данных в заданном потоке.  
  
 Подкоманды **ProcessOff** и **ProcessOn** также влияют на количество запусков и остановки процесса, которое задается функциями интерфейса API профилирования.  
  
-   Подкоманда **ProcessOff** непосредственно задает количество запусков и остановок процесса равным 0, вследствие чего процесс профилирования приостанавливается.  
  
-   Подкоманда **ProcessOn** непосредственно задает количество запусков и остановок процесса равным 1, вследствие чего процесс профилирования возобновляется.  
  
 Для получения дополнительной информации см. [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md).  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### Параметры  
 `PID`  
 Целочисленный идентификатор запускаемого или останавливаемого процесса.  Идентификаторы процесса перечисляются на вкладке "Процесс" диспетчера задач Windows.  
  
## Необходимые подкоманды  
 Нет  
  
## Допустимые подкоманды  
 Параметры **ProcessOn** и **ProcessOff** могут быть заданы в командной строке, содержащей следующие подкоманды.  
  
 **Start:** `Method`  
 Инициализирует сеанс профилирования из командной строки и задает указанный метод профилирования.  
  
 **Launch:** `AppName`  
 Запускает заданное приложение и начинает профилирование с помощью метода выборки.  
  
 **Attach:** `PID`  
 Начинает профилирование заданного процесса.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Начинает или останавливает профилирование для всех процессов сеанса профилирования из командной строки.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Останавливает или запускает профилирование заданного потока \(только метод инструментирования\).  
  
## Пример  
 В данном примере подкоманда **ProcessOff** используется для сбора данных профилирования для запуска приложения.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)