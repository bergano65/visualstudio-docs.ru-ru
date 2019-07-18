---
title: GC (VSPerfCmd) | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50b2e269ec292aaf37b8d0c707fa27ff8268a1f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969712"
---
# <a name="gc-vsperfcmd"></a>Параметр GC (VSPerfCmd)
Параметр **GC** включает сбор данных о выделении памяти и времени существования объектов. Параметр **GC** можно использовать только с методом профилирования с выборкой и только с параметром **Launch**.

 При использовании параметра **GC** команда VSPerfClrEnv **/sampleon** не требуется.

 Если параметры не указаны или указан параметр **Allocation**, собираются только данные о выделения памяти .NET Framework. Если указан параметр **Lifetime**, собираются данные о выделении памяти и времени существования объектов .NET Framework.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Параметры
 **Распределение**. По умолчанию. Собирает данные о выделении памяти .NET Framework.

 **Время существования**. Собирает данные о выделении памяти и времени существования объектов .NET Framework.

## <a name="required-options"></a>Обязательные параметры
 Параметр **GC** может использоваться только с параметром **Launch**.

 **Launch:** `AppName` Запускает заданное приложение и начинает профилирование с помощью метода выборки.

## <a name="example"></a>Пример
 Следующий пример запускает приложение и собирает данные о выделении памяти .NET Framework.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)