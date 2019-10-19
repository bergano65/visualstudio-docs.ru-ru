---
title: -Deploy (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 620be9ea458d55a8c9610079b357cc9466a03f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660771"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Развертывает решения после сборки или перестроения. Применяется только к проектам с управляемым кодом.

## <a name="syntax"></a>Синтаксис

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Аргументы
 `SolnConfigName` Обязательный. Имя конфигурации решения, которая будет применяться для сборки решения, указанного в `SolutionName`.

 `SolutionName` Обязательный. Полный путь и имя для файла решения.

 /project `ProjName` Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.

 /projectconfig `ProjConfigName` Необязательный. Имя конфигурации сборки проекта, которая применяется при сборке указанного `/project`.

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
 [Команды devenv параметры командной строки](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv](../../ide/reference/project-devenv-exe.md) . exe) [/Build (](../../ide/reference/build-devenv-exe.md) devenv. exe) [/Clean (](../../ide/reference/clean-devenv-exe.md) devenv. exe) [/REBUILD (](../../ide/reference/rebuild-devenv-exe.md) devenv. exe) [/out (devenv. exe](../../ide/reference/out-devenv-exe.md) )
