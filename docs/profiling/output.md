---
title: Параметр Output | Документы Майкрософт
description: Сведения о параметре Output, который задает имя файла данных профилирования для сеанса профилирования. Параметр Output должен использоваться с параметром Start.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6067e13e33875be778ff59739f5511c4116937ed
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722806"
---
# <a name="output"></a>Выходные данные
Параметр **Output** задает имя файла данных профилирования для сеанса профилирования. Параметр **Output** должен использоваться с параметром **Start**.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Параметры
 `FileName` Имя файла данных. Допускаются полные или частичные пути. Если путь не указан, файл создается в текущем каталоге.

## <a name="required-options"></a>Обязательные параметры
 Параметр **Output** используется с параметром **Start**.

 **Start:** `Method` Задает имя выходного файла.

## <a name="example"></a>Пример
 В этом примере файл данных профилирования создается в текущем каталоге.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
