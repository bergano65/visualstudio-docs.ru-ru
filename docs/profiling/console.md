---
title: Параметр Console | Документы Майкрософт
description: Используйте параметр Console программы VSPerfCmd.exe для запуска указанного приложения в новом окне командной строки. Его необходимо использовать с параметром Launch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 93c39bfb503bec9858e33b7acf04e0f0433264b9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720909"
---
# <a name="console"></a>Консоль
Параметр **Console** программы VSPerfCmd.exe запускает указанное приложение в новом окне командной строки. Параметр **Console** можно использовать только вместе с параметром **Launch** программы VSPerfCmd. Если приложение не является приложением командной строки, параметр **Console** ни на что не влияет.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Параметры
 Отсутствуют

## <a name="required-options"></a>Обязательные параметры
 Параметр **Console** можно указывать только в командной строке, в которой также содержится параметр **Launch**.

 **Launch:** `AppName` Запускает профилировщик и приложение, заданное параметром `AppName`.

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
