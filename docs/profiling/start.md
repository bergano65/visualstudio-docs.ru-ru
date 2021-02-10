---
title: Start | Документы Майкрософт
description: Сведения о параметре Start программы VSPerfCmd.exe, который инициализирует профилировщик для использования указанного метода профилирования.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98c1fa8a5d95b9819c6b988282fe9fcdb6259bd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960062"
---
# <a name="start"></a>Начать
**Start** — это параметр программы *VSPerfCmd.exe*, который инициализирует профилировщик для использования указанного метода профилирования.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Параметры
 `Method` Должен иметь в качестве значения одно из следующих ключевых слов:

- **TRACE** — задает метод инструментирования;

- **SAMPLE** — задает метод выборки;

- **COVERAGE** — задает объем протестированного кода;

- **CONCURRENCY** — задает метод состязания за ресурсы.

## <a name="required-options"></a>Обязательные параметры
 Если в командной строке задан параметр **Start**, необходимо указать параметр **Output**.

 **Выходные данные:** `filename` Задает имя выходного файла.

## <a name="exclusive-options"></a>Монопольные параметры
 Указанные ниже параметры могут использоваться только с параметром **Start** в командной строке.

 **CrossSession**&#124;**CS** включает профилирование в нескольких процессах. Поддерживаются оба имени параметра: **CrossSession** и **CS**.

 **User:** [`domain\`]`username` позволяет клиентам получать доступ к монитору с помощью указанной учетной записи.

 **WinCounter:** `Path` [**Automark**:`n`] **WinCounter** задает счетчик производительности Windows, который включается в файл данных профилирования в виде метки. **AutoMark** задает интервал в миллисекундах между сборами файла данных.

## <a name="invalid-options"></a>Недопустимые параметры
 Указанные ниже параметры не могут использоваться с параметром **Start** в командной строке.

 **Status. Параметр** **Status** применяется к процессам, для которых выполняется профилирование. Этот параметр перечисляет процессы и потоки и их текущее состояние профилирования (On/Off). Например, если процесс остановлен, параметр **Status** не отразит это в отчете. **Status** показывает, выполняется ли профилирование для процесса или нет.

 **Shutdown**[ **:** `Timeout`] отключает профилировщик.

## <a name="example"></a>Пример
 В приведенном ниже примере кода показано, как с помощью параметра **Start** программы *VSPerfCmd.exe* инициализировать профилировщик.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
