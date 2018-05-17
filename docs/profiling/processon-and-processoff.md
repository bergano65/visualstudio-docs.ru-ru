---
title: Подкоманды ProcessOn и ProcessOff | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f90e33d17e5f54066b038da36611329bb7169de4
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2018
---
# <a name="processon-and-processoff"></a>Подкоманды ProcessOn и ProcessOff
Подкоманды **ProcessOff** и **ProcessOn** программы VSPerfCmd.exe приостанавливают и возобновляют профилирование заданного процесса в сеансе профилирования из командной строки. **ProcessOff** останавливает профилирование процесса, а **ProcessOn** запускает его.  
  
 В большинстве случаев параметр **ProcessOn** или **ProcessOff** можно задать как единственный параметр программы VSPerfCmd.exe в командной строке либо в сочетании с подкомандами **GlobalOn**, **GlobalOff**, **ThreadOn** и **ThreadOff**.  
  
 Подкоманды **ProcessOn** и **ProcessOff** взаимодействуют с подкомандами **GlobalOn** и **GlobalOff**, которые управляют сбором данных для всех процессов сеанса профилирования с использованием командной строки, и с подкомандами **ThreadOn** и **ThreadOff**, которые позволяют управлять сбором данных для указанного потока.  
  
 Подкоманды **ProcessOff** и **ProcessOn** также влияют на количество запусков и остановок процесса, которое задается функциями интерфейса API профилирования.  
  
-   Подкоманда **ProcessOff** непосредственно задает количество запусков и остановок процесса равным 0, вследствие чего профилирование приостанавливается.  
  
-   Подкоманда **ProcessOn** непосредственно задает количество запусков и остановок процесса равным 1, вследствие чего профилирование возобновляется.  
  
 Дополнительные сведения см. в статье [Profiling Tools APIs](../profiling/profiling-tools-apis.md) (Интерфейсы API для средств профилирования).  
  
## <a name="syntax"></a>Синтаксис  
  
```cmd  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `PID`  
 Целочисленный идентификатор запускаемого или останавливаемого процесса. Идентификаторы процессов приводятся на вкладке "Процесс" диспетчера задач Windows.  
  
## <a name="required-subcommands"></a>Необходимые подкоманды  
 Нет  
  
## <a name="valid-subcommands"></a>Допустимые подкоманды  
 Подкоманды **ProcessOn** и **ProcessOff** можно задать в командной строке, содержащей указанные ниже подкоманды.  
  
 **Start:** `Method`  
 Инициализирует сеанс профилирования из командной строки и задает указанный метод профилирования.  
  
 **Launch:** `AppName`  
 Запускает заданное приложение и начинает профилирование с помощью метода выборки.  
  
 **Attach:** `PID`  
 Начинает профилирование указанного процесса.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Начинает или останавливает профилирование для всех процессов сеанса профилирования из командной строки.  
  
 {**ThreadOff** | **ThreadOn**}**:**`TID`  
 Останавливает или запускает профилирование заданного потока (только метод инструментирования).  
  
## <a name="example"></a>Пример  
 В этом примере подкоманда **ProcessOff** используется для сбора данных профилирования для запуска приложения.  
  
```cmd  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)