---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93d3e4323638d40f003247a2c5bd35c812cc1c69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Регистрирует все действия в файле журнала для устранения неполадок. Этот файл отображается после вызова `devenv /log` по крайней мере один раз. Файл журнала по умолчанию:

 *%APPDATA%* \Microsoft\VisualStudio\\*Версия*\ActivityLog.xml

 где *Версия* — это версия Visual Studio. Однако можно указать альтернативный путь и имя файла.

## <a name="syntax"></a>Синтаксис

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Примечания
 Этот ключ должен находиться в конце командной строки после всех других параметров.

 Журнал записывается для всех экземпляров Visual Studio, которые были активированы с ключом /log. Для экземпляров Visual Studio, которые были активированы без данного ключа, журнал не записывается.

## <a name="see-also"></a>См. также

- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)