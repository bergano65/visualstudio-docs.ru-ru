---
title: Параметр User (VSPerfCmd) | Документы Майкрософт
description: Сведения о параметре User, указывающем домен и имя пользователя учетной записи, которая является владельцем профилируемого процесса.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b0240a4dcf0830dca6667bcbd055d677ef7bc204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886006"
---
# <a name="user-vsperfcmd"></a>Параметр User (VSPerfCmd)
Параметр **User** указывает домен и имя пользователя учетной записи, которая является владельцем профилируемого процесса. Этот параметр является обязательным только в том случае, если процесс выполняется в качестве пользователя, отличного от пользователя, вошедшего в систему. Владелец процесса указан в столбце "Имя пользователя" на вкладке **Процессы** диспетчера задач Windows.

 Параметр **User** можно указывать только в командной строке, которая также содержит параметр **Start**.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Параметры
 `Domain` Имя домена пользователя.

 `UserName` Имя пользователя.

## <a name="required-options"></a>Обязательные параметры
 Параметр **User** можно использовать только вместе с параметром **Start**.

 **Start:** `Method` Инициализирует профилировщик для заданного метода профилирования.

## <a name="example"></a>Пример
 Следующий пример иллюстрирует использование параметра **User**.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
