---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab5ba4756a24405c6cf531452395235b7f4d6db7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949877"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Регистрирует все действия в файле журнала для устранения неполадок. Этот файл отображается после вызова `devenv /log` по крайней мере один раз. Файл журнала по умолчанию расположен здесь:

**%APPDATA%\\Microsoft\\VisualStudio\\**\<Version\>**\\ActivityLog.xml**

где \<Версия\> — это версия Visual Studio. Однако можно указать альтернативный путь и имя файла.

## <a name="syntax"></a>Синтаксис

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Аргументы

- *NameOfLogFile*

  Обязательный. Полный путь и имя файла для сохранения.

## <a name="remarks"></a>Примечания

Этот ключ должен находиться в конце командной строки после всех других параметров.

Журнал записывается только для всех экземпляров Visual Studio, которые были активированы с использованием параметра `/Log`.

## <a name="example"></a>Пример

Этот пример выбирает для ведения журнала файл `MyVSLog.xml` в домашнем каталоге пользователя.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)