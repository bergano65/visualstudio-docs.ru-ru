---
title: Параметр Console | Документы Майкрософт
description: Используйте параметр Console программы VSPerfCmd.exe для запуска указанного приложения в новом окне командной строки. Его необходимо использовать с параметром Launch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a5234c2b7368a992676e12ecbdcd5ea36219f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955415"
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
