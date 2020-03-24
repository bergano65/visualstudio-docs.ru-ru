---
title: Параметры GlobalOn и GlobalOff | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 518f41557809cdeaaae9f9e1ac79e3797a854395
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776970"
---
# <a name="globalon-and-globaloff"></a>Параметры GlobalOn и GlobalOff
Параметры **GlobalOff** и **GlobalOn** средства *VSPerfCmd.exe* позволяют приостанавливать и возобновлять профилирование для всех процессов и потоков в сеансе профилирования, управляемом из командной строки.

 Параметры **GlobalOn** и **GlobalOff** можно использовать как единственные параметры в командной строке *VSPerfCmd.exe* или включать в командную строку, содержащую параметры **Start**, **Launch** или **Attach**.

 Параметры **GlobalOn** и **GlobalOff** также могут сочетаться с параметрами **ProcessOn**, **ProcessOff**, **ThreadOn** и **ThreadOff**.

 Параметры **GlobalOn** и **GlobalOff** взаимодействуют с параметрами **ProcessOn** и **ProcessOff**, которые управляют сбором данных в заданном процессе, а также с параметрами **ThreadOn** и **ThreadOff**, которые управляют сбором данных для указанного потока.

 Также параметры **GlobalOff** и **GlobalOn** влияют на глобальный счетчик запусков и остановок, который управляется функциями API профилировщика.

- **GlobalOff** немедленно устанавливает значение 0 для глобального счетчика запусков и остановок, вследствие чего процесс профилирования приостанавливается.

- **GlobalOn** немедленно устанавливает значение 1 глобального счетчика запусков и остановок, вследствие чего процесс профилирования возобновляется.

  Дополнительные сведения см. в статье [Интерфейсы API для средств профилирования](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Параметры
 Отсутствуют

## <a name="valid-options"></a>Допустимые параметры
 **GlobalOn** и **GlobalOff** можно использовать в командной строке, которая содержит следующие параметры.

 **Start:** `Method` Инициализирует сеанс командной строки для профилировщика и задает метод профилирования.

 **Launch:** `AppName` Запускает заданное приложение и начинает профилирование с помощью метода выборки.

 **Attach:** `PID` Начинает профилирование указанного процесса.

 {**ProcessOff** | **ProcessOn**}**:**`PID` Останавливает или запускает профилирование указанного процесса.

 {**ThreadOff** | **ThreadOn**}**:**`TID` Останавливает или запускает профилирование заданного процесса (только для метода инструментирования).

## <a name="example"></a>Пример
 В этом примере **GlobalOff** и **GlobalOn** используются для того, чтобы не собирать данные профилирования в процессе запуска и завершения работы приложения.

```cmd
; Initialize the profiler with profiling stopped.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff
; Start an instrumented application and wait for it to warm up.
; Start profiling.
VSPerfCmd.exe /GlobalOn
; Exercise the application functionality that you want to profile.
; Stop profiling.
VSPerfCmd.exe /GlobalOff
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
