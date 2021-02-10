---
title: Параметр Mark | Документы Майкрософт
description: Сведения о том, как параметр Mark программы VSPerfCmd.exe вставляет указанные сведения в файл данных профилирования.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 33a343be010a5bf9cc0d9ba3e4251d92fd720656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917807"
---
# <a name="mark"></a>Метка
Параметр **Mark** программы *VSPerfCmd.exe* вставляет указанные сведения в файл данных профилирования. Метка может быть указана в отдельном отчете VSPerfReport или в представлении отчета "Метки" пользовательского интерфейса профилировщика. Параметр **Mark** можно использовать для указания начальных и конечных точек в фильтрах отчетов и представлений.

 Параметр **Mark** должен быть единственным параметром, указанным в командной строке.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Параметры
 `MarkID` Определенное пользователем целое число, указанное в качестве идентификатора метки в представлениях и отчетах профилировщика. Идентификатор `MarkID` необязательно должен быть уникальным.

 `MarkName` Определенная пользователем строка, указанная в качестве имени метки в представлениях и отчетах профилировщика (необязательно). Если параметр `MarkName` не задан, поле "Имя метки" в списке остается пустым. Строки, содержащие пробелы или косую черту ("/"), заключаются в кавычки.

## <a name="example"></a>Пример
 В этом примере вставляется метка с идентификатором 123 и именем TestMark.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
