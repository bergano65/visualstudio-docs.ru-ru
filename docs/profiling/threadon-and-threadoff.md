---
title: Подкоманды ThreadOn и ThreadOff | Документы Майкрософт
description: Сведения о подкомандах ThreadOff и ThreadOn программы VSPerfCmd.exe, доступных только в сеансах профилирования из командной строки, в которых используется метод инструментирования.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 059e7dfc9d7c16be3aa699eea47b1a64882e689e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949315"
---
# <a name="threadon-and-threadoff"></a>Параметры ThreadOn и ThreadOff
Подкоманды **ThreadOff** и **ThreadOn** программы *VSPerfCmd.exe* доступны только в сеансах профилирования из командной строки, в которых используется метод инструментирования. **ThreadOff** и **ThreadOn** приостанавливают и возобновляют профилирование для указанного потока. **ThreadOff** останавливает профилирование потока, а **ThreadOn** запускает его.

 В большинстве случаев **ThreadOn** или **ThreadOff** указывается как единственный параметр команды *VSPerfCmd.exe*, но их также можно сочетать с подкомандами **GlobalOn**, **GlobalOff**, **ProcessOn** и **ProcessOff**.

 Подкоманды **ThreadOn** и **ThreadOff** взаимодействуют с подкомандами **GlobalOn** и **GlobalOff**, которые управляют сбором данных для всех процессов сеанса профилирования с использованием командной строки, и с подкомандами **ProcessOn** и **ProcessOff**, которые позволяют управлять сбором данных для указанного процесса.

 Подкоманды **ThreadOff** и **ThreadOn** также влияют на количество запусков и остановок потока, которое задается функциями интерфейса API профилирования.

- **ThreadOff** немедленно устанавливает значение 0 для счетчика запусков и остановок потока, вследствие чего профилирование приостанавливается.

- **ThreadOn** немедленно устанавливает значение 1 для счетчика запусков и остановок потока, вследствие чего профилирование возобновляется.

  Дополнительные сведения см. в статье [Интерфейсы API для средств профилирования](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Параметры
 `TID` Целочисленный идентификатор запускаемого или останавливаемого потока.

## <a name="valid-options"></a>Допустимые параметры
 Подкоманды **ThreadOnn** и **ThreadOff** можно задать в командной строке, содержащей указанные ниже подкоманды.

 **Start:** `Method` Инициализирует сеанс профилирования из командной строки и задает указанный метод профилирования.

 **GlobalOff**&#124;**GlobalOn** начинает или останавливает профилирование для всех процессов сеанса профилирования из командной строки.

 {**ProcessOff** | **ProcessOn**} **:** `TID` Останавливает или запускает профилирование указанного процесса.

## <a name="example"></a>Пример
 В этом примере подкоманда **ThreadOff** используется для остановки сбора данных профилирования, в результате чего выполняется только сбор данных по запуску приложения.

```cmd
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
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
