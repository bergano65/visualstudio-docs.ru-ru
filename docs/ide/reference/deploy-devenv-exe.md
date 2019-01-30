---
title: -Deploy (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0eef6420f09157a349658ca232a9e2551476b9d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008482"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Развертывает решения после сборки или перестроения. Применяется только к проектам с управляемым кодом.

## <a name="syntax"></a>Синтаксис

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Аргументы

- *SolutionName*

  Обязательный. Полный путь и имя для файла решения.

- *SolnConfigName*

  Необязательный параметр. Имя конфигурации решения (например, `Debug` или `Release`) для использования при сборке решения, указанного в *SolutionName*. Если доступно несколько платформ решений, необходимо также указать платформу (например, `Debug|Win32`). Если этот аргумент не определен или является пустой строкой (`""`), используется действующая конфигурация решения.

- `/Project` *ProjName*

  Необязательный параметр. Путь и имя для файла проекта в решении. Можно ввести отображаемое имя проекта или относительный путь из папки *SolutionName* к файлу проекта. Можно также ввести полный путь и имя файла проекта.

- `/ProjectConfig` *ProjConfigName*

  Необязательный параметр. Имя конфигурации сборки проекта (например, `Debug` или `Release`) для использования при сборке указанного проекта `/Project`. Если доступно несколько платформ решений, необходимо также указать платформу (например, `Debug|Win32`). Если этот параметр задан, он переопределяет аргумент *SolnConfigName*.

- `/Out` *OutputFilename*

  Необязательный параметр. Имя файла, в который вы хотите отправить выходные данные средства. Если файл уже существует, средство добавляет в его конец выходные данные.

## <a name="remarks"></a>Примечания

Указанный проект должен быть проектом развертывания. В противном случае при передаче созданного проекта для развертывания возникает ошибка.

Строки с пробелами заключаются в двойные кавычки.

Сводные данные по сборкам, включая ошибки, могут отображаться в окне **Команда** или в любом файле журнала, указанном с помощью параметра [/Out](out-devenv-exe.md).

## <a name="example"></a>Пример

Этот пример развертывает проект `CSharpWinApp` с использованием конфигурации сборки проекта `Release` в решении `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)