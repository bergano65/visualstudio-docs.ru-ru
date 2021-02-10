---
title: WaitStart | Документация Майкрософт
description: Сведения о параметре WaitStart, благодаря которому подкоманда Start программы VSPerfCmd.exe возвращается только после инициализации профилировщика или через указанное число секунд.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b883ae215854994918419fb311d94ad921989740
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911483"
---
# <a name="waitstart"></a>WaitStart
Благодаря параметру WaitStart подкоманда *VSPerfCmd.exe* Start возвращается только после инициализации профилировщика или через указанное число секунд. По умолчанию команда Start возвращается немедленно. Если подкоманда Start возвращается без инициализации профилировщика, возвращается ошибка. Если не указано число секунд, команда Start ожидает неограниченное время.

 Параметр WaitStart полезно использовать в пакетных файлах, чтобы обеспечивать инициализацию профилировщика.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Параметры
 `Seconds` Число секунд ожидания перед возвращением подкоманды Start.

## <a name="required-options"></a>Обязательные параметры
 Параметр WaitStart может использоваться только с подкомандой Start.

 **Выходные данные:** `filename` Задает имя выходного файла.

## <a name="remarks"></a>Remarks

## <a name="example"></a>Пример
 В этом примере пакетного файла команда Start ожидает инициализацию профилировщика 5 секунд.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5
if not %errorlevel% 0 goto :error_tag
VSPerfCmd.exe /Launch:TestApp.exe
goto :end
:error_tag
@echo Could not start Profiler!
@echo Error %errorlevel%
:end
```
