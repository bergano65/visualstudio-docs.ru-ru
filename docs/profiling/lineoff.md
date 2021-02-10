---
title: Параметр LineOff | Документы Майкрософт
description: Сведения о параметре LineOff команды VSPerfCmd, который отключает сбор данных по номерам строк, когда команда VSPerfCmd используется для запуска приложения.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a141e713dd03f99db6ce47224c64236a0219cdd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917906"
---
# <a name="lineoff"></a>LineOff
При использовании метода профилирования с выборкой профилировщик по умолчанию собирает сведения о количестве строк исходного кода и смещении номеров строк. Параметр **LineOff** команды VSPerfCmd отключает сбор данных по номерам строк, когда команда VSPerfCmd используется для запуска приложения. Если задан параметр **LineOff**, данные профилирования собираются до уровня функции.

 Параметр **LineOff** можно использовать только с параметром **Launch** и только в том случае, если профилировщик был инициализирован для выборки с помощью параметра **Start**:**Sample**.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Параметры
 Отсутствуют

## <a name="required-options"></a>Обязательные параметры
 Параметр **LineOff** можно использовать только в команде, в которой также содержится параметр **Launch**.

 **Launch:** `AppName` Запускает заданное приложение и начинает профилирование с помощью метода выборки.

## <a name="example"></a>Пример
 В этом примере запускаются приложение и профилировщик и отключается выборка на уровне строк.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
