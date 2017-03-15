---
title: "Параметры ThreadOn и ThreadOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Параметры ThreadOn и ThreadOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Подкоманды **ThreadOff** и **ThreadOn** программы VSPerfCmd.exe доступны только в сеансах профилирования командной строки, в которых используется метод инструментирования.  **ThreadOff** и **ThreadOn** приостанавливают и возобновляют профилирование для указанного потока.  **ThreadOff** останавливает профилирование потока, а **ThreadOn** запускает профилирование потока.  
  
 В большинстве случаев параметр **ThreadOn** или **ThreadOff** можно задать как единственный параметр команды VSPerfCmd.exe либо включить их в команды, которые также содержат параметры **GlobalOn**, **GlobalOff**, **ProcessOn** и **ProcessOff**.  
  
 Параметры **ThreadOn** и **ThreadOff** также взаимодействуют с параметрами **GlobalOn** и **GlobalOff**, которые управляют сбором данных для всех процессов сеанса профилирования с использованием командной строки, и с параметрами **ProcessOn** и **ProcessOff**, которые управляют сбором данных в заданном процессе.  
  
 Параметры **ThreadOff** и **ThreadOn** также влияют на количество команд начала и остановки потока, которое управляется функциями интерфейса API профилирования.  
  
-   Параметр **ThreadOff** немедленно устанавливает значение числа команд начала и остановки потока, равное 0, вследствие чего процесс профилирования приостанавливается.  
  
-   Параметр **ThreadOn** немедленно устанавливает значение числа команд начала и остановки потока, равное 1, вследствие чего процесс профилирования возобновляется.  
  
 Для получения дополнительной информации см. [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md).  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### Параметры  
 `TID`  
 Целочисленный идентификатор запускаемого или останавливаемого потока.  
  
## Допустимые параметры  
 Параметры **ThreadOn** и **ThreadOff** могут быть заданы в командах, которые также содержат следующие подкоманды.  
  
 **Start:** `Method`  
 Инициализирует сеанс профилирования из командной строки и задает указанный метод профилирования.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Начинает или останавливает профилирование для всех процессов сеанса профилирования из командной строки.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Останавливает или запускает профилирование заданного процесса.  
  
## Пример  
 В данном примере подкоманда **ThreadOff** используется для остановки сбора данных профилирования, в результате чего выполняется только сбор данных о запуске приложения.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)