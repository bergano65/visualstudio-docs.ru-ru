---
title: -Build (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 419716d750771908a43318d051cb0b4681d35149
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660984"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Выполняет сборку решения с использованием заданного файла конфигурации решения.

## <a name="syntax"></a>Синтаксис

```
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

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>См. также
 [Создание и очистка проектов и решений в Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [Параметры командной строки devenv](../../ide/reference/devenv-command-line-switches.md) [/REBUILD (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Clean (](../../ide/reference/clean-devenv-exe.md) devenv. exe) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
