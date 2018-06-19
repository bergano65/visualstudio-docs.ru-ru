---
title: -Deploy (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 368680321f8ff8ab908e79e075a5797ba9ecd598
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945120"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
Развертывает решения после сборки или перестроения. Применяется только к проектам с управляемым кодом.

## <a name="syntax"></a>Синтаксис

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Аргументы
 `SolnConfigName`

 Обязательно. Имя конфигурации решения, которая будет применяться для сборки решения, указанного в `SolutionName`.

 `SolutionName`

 Обязательно. Полный путь и имя для файла решения.

 /project `ProjName`

 Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.

 /projectconfig `ProjConfigName`

 Необязательный. Имя конфигурации сборки проекта, которая применяется при сборке указанного `/project`.

## <a name="remarks"></a>Примечания
 Указанный проект должен быть проектом развертывания. В противном случае при передаче собранного проекта для развертывания возникает ошибка.

 Строки с пробелами заключаются в двойные кавычки.

 Сводные данные для сборок, включая ошибки, могут отображаться в окне **команд** или в любом файле журнала, указанном с помощью параметра `/out`.

## <a name="example"></a>Пример
 Этот пример развертывает проект `CSharpConsoleApp` с использованием конфигурации сборки проекта `Release` в пределах конфигурация решения `Release` для `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)