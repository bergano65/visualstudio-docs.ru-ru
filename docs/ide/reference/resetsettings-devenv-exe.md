---
title: -ResetSettings (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3549801001ba8df60634884dc58137a8fa77d905
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655568"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Восстанавливает параметры по умолчанию Visual Studio и автоматически запускает интегрированную среду разработки Visual Studio. При необходимости выполняет сброс параметров в соответствии с указанным файлом параметров.

Параметры определяются профилем, который был выбран при первом запуске Visual Studio.

> [!TIP]
> Дополнительные сведения о сбросе параметров с помощью интегрированной среды разработки (IDE) см. в разделе [Сброс параметров](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Синтаксис

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Аргументы

- *SettingsFile*

  Необязательный параметр. Полный путь и имя файла параметров, применяемого к Visual Studio.

- *DefaultCollectionSpecifier*

  Необязательный параметр. Описатель, представляющий коллекцию параметров для восстановления по умолчанию. Выберите один из перечисленных в таблице описателей коллекции по умолчанию.

  | Имя коллекции по умолчанию | Описатель коллекции |
  | --- | --- |
  | **Общие сведения** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Веб-разработка** | `Web` |
  | **Веб-разработка (только код)** | `WebCode` |

## <a name="remarks"></a>Примечания

Если файл *SettingsFile* не указан, интегрированная среда разработки открывается с использованием существующих параметров.

## <a name="example"></a>Пример

Первый пример применяет параметры, сохраненные в файле `MySettings.vssettings`.

Второй пример восстанавливает профиль Visual C# по умолчанию.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>См. также

- [Параметры среды](../environment-settings.md)
- [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)