---
title: -ResetSettings (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c3d3a6ef558b510cfde716716daf97a549fbba4
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Восстанавливает параметры по умолчанию Visual Studio и автоматически запускает интегрированную среду разработки Visual Studio. При необходимости выполняет сброс параметров в соответствии с указанным файлом *VSSETTINGS*.

Параметры по умолчанию определяются по профилю, который был выбран при первом запуске Visual Studio.

## <a name="syntax"></a>Синтаксис

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Аргументы

`SettingsFile`

Полный путь и имя файла *VSSETTINGS*, применяемого к Visual Studio.

Чтобы восстановить профиль "Общие параметры разработки", используйте `General`.

## <a name="remarks"></a>Примечания

Если файл `SettingsFile` не указан, при следующем запуске Visual Studio вам предлагается выбрать коллекцию параметров по умолчанию.

## <a name="example"></a>Пример

Следующая команда применяет параметры, сохраненные в файле `MySettings.vssettings`.

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>См. также

- [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)