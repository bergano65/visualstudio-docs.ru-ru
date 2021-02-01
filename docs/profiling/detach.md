---
title: Параметр Detach | Документы Майкрософт
description: Параметр Detach программы VSPerfCmd.exe отключает профилировщик от заданных процессов или от всех процессов, если процессы не заданы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45225e4478b0a1a3cddc7f74ae223c437bf4226e
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686601"
---
# <a name="detach"></a>Detach
Параметр **Detach** программы VSPerfCmd.exe отключает профилировщик от заданных процессов или от всех процессов, если процессы не заданы. Для инициализации профилирования нужно использовать метод выборки.

 Профилирование, запущенное с параметром **Launch** или **Attach**, можно отключить с помощью параметра **Detach**. Для повторного подключения профилировщика можно воспользоваться командами **Attach**.

 Параметр **Detach** не приводит к закрытию файла данных профилирования. Чтобы завершить профилирование и закрыть файл данных, воспользуйтесь параметром **Shutdown**.

> [!NOTE]
> Если параметр **Start** был задан с параметром **Crosssession**, во всех вызовах команды **VSPerfCmd /Attach** или **VSPerfCmd /Detach** также должен быть указан параметр **Crosssession**.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Параметры
 `PIDs|ProcessNames` `PID` — числовой системный идентификатор одного или нескольких процессов.

 `ProcessNames` — имя процесса. Если запущено несколько экземпляров именованного процесса, результат будет непредсказуемым.

 Разделяйте процессы запятыми.

 Если процесс не задан, профилировщик отключится от всех профилируемых процессов.

## <a name="valid-options"></a>Допустимые параметры
 Указанные ниже параметры программы **VSPerfCmd** могут сочетаться с параметром **Attach** в одной командной строке.

 **Crosssession** включает профилирование приложений в сеансах, отличных от сеанса входа в систему. Является обязательным, если параметр **Start** был задан с параметром **Crosssession**.

## <a name="example"></a>Пример
 В этом примере команда **Detach** приостанавливает профилирование, а команда **Shutdown** закрывает файл данных профилировщика.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
