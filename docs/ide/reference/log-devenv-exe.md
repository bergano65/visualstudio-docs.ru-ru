---
title: -Log (devenv.exe)
ms.date: 12/12/2018
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
ms.openlocfilehash: 4b2e11cb36176aec94528019cdd19bb5fa86c92b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907221"
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