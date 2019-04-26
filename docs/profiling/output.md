---
title: Параметр Output | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78d5b39908bc0ffa39533c22ea4effcbe97397b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62794221"
---
# <a name="output"></a>Вывод
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