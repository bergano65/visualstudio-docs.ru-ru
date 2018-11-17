---
title: Подкоманды ThreadOn и ThreadOff | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e908da955258bfef5d66187bc974b6e051a48ad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789178"
---
# <a name="threadon-and-threadoff"></a>Параметры ThreadOn и ThreadOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Подкоманды **ThreadOff** и **ThreadOn** программы VSPerfCmd.exe доступны только в сеансах профилирования из командной строки, в которых используется метод инструментирования. **ThreadOff** и **ThreadOn** приостанавливают и возобновляют профилирование для указанного потока. **ThreadOff** останавливает профилирование потока, а **ThreadOn** запускает его.  
  
 В большинстве случаев **ThreadOn** или **ThreadOff** указывается как единственный параметр команды VSPerfCmd.exe, но их также можно сочетать с подкомандами **GlobalOn**, **GlobalOff**, **ProcessOn** и **ProcessOff**.  
  
 Подкоманды **ThreadOn** и **ThreadOff** взаимодействуют с подкомандами **GlobalOn** и **GlobalOff**, которые управляют сбором данных для всех процессов сеанса профилирования с использованием командной строки, и с подкомандами **ProcessOn** и **ProcessOff**, которые позволяют управлять сбором данных для указанного процесса.  
  
 Подкоманды **ThreadOff** и **ThreadOn** также влияют на количество запусков и остановок потока, которое задается функциями интерфейса API профилирования.  
  
- **ThreadOff** немедленно устанавливает значение 0 для счетчика запусков и остановок потока, вследствие чего профилирование приостанавливается.  
  
- **ThreadOn** немедленно устанавливает значение 1 для счетчика запусков и остановок потока, вследствие чего профилирование возобновляется.  
  
  Дополнительные сведения см. в статье [Profiling Tools APIs](../profiling/profiling-tools-apis.md) (Интерфейсы API для средств профилирования).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `TID`  
 Целочисленный идентификатор запускаемого или останавливаемого потока.  
  
## <a name="valid-options"></a>Допустимые параметры  
 Подкоманды **ThreadOnn** и **ThreadOff** можно задать в командной строке, содержащей указанные ниже подкоманды.  
  
 **Start:** `Method`  
 Инициализирует сеанс профилирования из командной строки и задает указанный метод профилирования.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Начинает или останавливает профилирование для всех процессов сеанса профилирования из командной строки.  
  
 {**ProcessOff** | **ProcessOn**}**:**`TID`  
 Останавливает или запускает профилирование указанного процесса.  
  
## <a name="example"></a>Пример  
 В этом примере подкоманда **ThreadOff** используется для остановки сбора данных профилирования, в результате чего выполняется только сбор данных по запуску приложения.  
  
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
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)



