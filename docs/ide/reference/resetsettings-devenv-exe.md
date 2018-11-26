---
title: -ResetSettings (devenv.exe)
ms.date: 11/16/2018
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
ms.openlocfilehash: 568a829ff10cbee535729361b7c95dd7db6814f5
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948073"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Восстанавливает параметры по умолчанию Visual Studio и автоматически запускает интегрированную среду разработки Visual Studio. При необходимости выполняет сброс параметров в соответствии с указанным файлом *VSSETTINGS*.

Параметры по умолчанию определяются по профилю, который был выбран при первом запуске Visual Studio.

> [!TIP]
> Дополнительные сведения о сбросе параметров с помощью интегрированной среды разработки (IDE) см. в разделе [Сброс параметров](../synchronized-settings-in-visual-studio.md#reset-settings).

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

- [Сброс параметров](../synchronized-settings-in-visual-studio.md#reset-settings)
- [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)