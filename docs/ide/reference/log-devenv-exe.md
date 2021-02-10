---
title: -Log (devenv.exe)
description: Узнайте, как использовать параметр командной строки Log devenv для регистрации всех действий в файле журнала для устранения неполадок.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7a4f8f3fc7fe0e0f8b7ff6bd460ea2efd8192d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919394"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Регистрирует все действия в файле журнала для устранения неполадок. Этот файл отображается после вызова `devenv /log` по крайней мере один раз. Файл журнала по умолчанию расположен здесь:

**%APPDATA%\\Microsoft\\VisualStudio\\** \<Version\> **\\ActivityLog.xml**

где \<Version\> — это версия Visual Studio. Однако можно указать альтернативный путь и имя файла.

## <a name="syntax"></a>Синтаксис

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Аргументы

- *NameOfLogFile*

  Обязательный элемент. Полный путь и имя файла для сохранения.

## <a name="remarks"></a>Remarks

Этот ключ должен находиться в конце командной строки после всех других параметров.

Журнал записывается только для всех экземпляров Visual Studio, которые были активированы с использованием параметра `/Log`.

## <a name="example"></a>Пример

Этот пример выбирает для ведения журнала файл `MyVSLog.xml` в домашнем каталоге пользователя.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
