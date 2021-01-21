---
title: Args | Документы Майкрософт
description: Используйте параметр ARGS программы VSPerfCmd.exe, чтобы передать список аргументов целевому приложению подкоманды Launch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ff16d67d0c7168524ff145183f49a662e1f660f0
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205714"
---
# <a name="args"></a>Args
Параметр **Args** VSPerfCmd.exe определяет список аргументов, которые передаются целевому приложению подкоманды **Launch**.

 **Args** можно использовать только при условии, если в командной строке также задан параметр **Launch**. Использовать **Args** не обязательно, если указан параметр **Launch**.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Параметры
 `Arguments`Список аргументов для целевого приложения команды **Launch**.

## <a name="required-options"></a>Обязательные параметры
 **Launch:** `AppName` Запускает заданное приложение и начинает профилирование с помощью метода выборки.

## <a name="example"></a>Пример
 В следующем примере параметр **Args** используется для передачи аргументов в TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
