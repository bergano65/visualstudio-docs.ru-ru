---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008e7ca15595db249c05485f0d9e8f8b1277993e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595466"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Регистрирует все действия в файле журнала для устранения неполадок. Этот файл отображается после вызова `devenv /log` по крайней мере один раз. Файл журнала по умолчанию расположен здесь:

**%APPDATA%\\Microsoft\\VisualStudio\\** \<Version\> **\\ActivityLog.xml**

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
