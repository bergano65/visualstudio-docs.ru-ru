---
title: -Build (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba1d23302cc0c3b9d14b23bd8547f33eb21ce0c3
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
Выполняет сборку решения с использованием заданного файла конфигурации решения.

## <a name="syntax"></a>Синтаксис

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Аргументы
 `SolutionName` Обязательный. Полный путь и имя для файла решения.

 `SolnConfigName` Обязательный. Имя конфигурации решения, которая будет применяться для сборки решения, указанного в `SolutionName`.

 /project `ProjName` Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.

 /projectconfig `ProjConfigName` Необязательный. Имя конфигурации сборки проекта, которая применяется при сборке указанного `/project`.

## <a name="remarks"></a>Примечания
 Этот параметр выполняет те же функции, что и команда меню **Собрать решение** в интегрированной среде разработки (IDE).

 Строки с пробелами заключаются в двойные кавычки.

 Сводные данные для сборок, включая ошибки, могут отображаться в окне **команд** или в любом файле журнала, указанном с помощью параметра `/out`.

 Эта команда выполняет сборку только тех проектов, которые изменились с момента последней сборки. Чтобы выполнить сборку всех проектов в решении, используйте [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md).

## <a name="example"></a>Пример
 В этом примере выполняется сборка проекта `CSharpConsoleApp` с использованием конфигурации проекта `Debug` в пределах конфигурация решения `Debug` для `MySolution`.

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>См. также

- [Построение и очистка проектов и решений в Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)