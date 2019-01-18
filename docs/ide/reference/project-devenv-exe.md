---
title: -Project (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /Project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- Project Devenv switch (/Project)
- Devenv, /Project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1706d8dade02bd7f247d7f2ce163955615a3b0f3
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269190"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Указывает отдельный проект в заданной конфигурации решения для сборки, очистки, перестроения или развертывания.

## <a name="syntax"></a>Синтаксис

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Аргументы

- *SolutionName*

  Обязательный. Полный путь и имя для файла решения.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Обязательный. [Создает](build-devenv-exe.md), [очищает](clean-devenv-exe.md), [развертывает](deploy-devenv-exe.md) или [повторно создает](rebuild-devenv-exe.md) проект.

- *SolnConfigName*

  Необязательный параметр. Имя конфигурации решения (например, `Debug` или `Release`) для применения в решении, указанном в *SolutionName*. Если доступно несколько платформ решений, необходимо также указать платформу (например, `Debug|Win32`). Если этот аргумент не определен или является пустой строкой (`""`), используется действующая конфигурация решения.

- `/Project` *ProjName*

  Необязательный параметр. Путь и имя для файла проекта в решении. Можно ввести отображаемое имя проекта или относительный путь из папки *SolutionName* к файлу проекта. Можно также ввести полный путь и имя файла проекта.

- `/ProjectConfig` *ProjConfigName*

  Необязательный параметр. Имя конфигурации сборки проекта (например, `Debug` или `Release`) для применения к указанному проекту `/Project`. Если доступно несколько платформ решений, необходимо также указать платформу (например, `Debug|Win32`).

- `/Out` *OutputFilename*

  Необязательный параметр. Имя файла, в который вы хотите отправить выходные данные средства. Если файл уже существует, средство добавляет в его конец выходные данные.

## <a name="remarks"></a>Примечания

- Следует использовать в составе команды `devenv` `/Build`, `/Clean`, `/Rebuild` или `/Deploy`.

- Строки с пробелами заключаются в двойные кавычки.

- Сводные данные для сборок, включая ошибки, могут отображаться в окне **команд** или в любом файле журнала, указанном с помощью параметра `/Out`.

## <a name="example"></a>Пример

Этот пример выполняет сборку проекта `CSharpWinApp` с использованием конфигурации сборки проекта `Debug` в решении `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)