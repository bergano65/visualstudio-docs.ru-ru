---
title: -Project (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9c54691ed343493ef1e43798faf4d2ab6f60fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662110"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает отдельный проект в заданной конфигурации решения для сборки, очистки, перестроения или развертывания.

## <a name="syntax"></a>Синтаксис

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName
[/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Аргументы
 /Build выполняет сборку проекта, указанного параметром `/project` `ProjName` .

 /Clean очищает все промежуточные файлы и выходные каталоги, созданные во время сборки.

 /Rebuild очищает проект, указанный в `/project` `ProjName` .

 /Deploy указывает, что проект должен быть развернут после сборки или перестроения.

 `SolnConfigName` Обязательный. Имя конфигурации решения, которая будет применяться для решения с именем `SolutionName`.

 `SolutionName` Обязательный. Полный путь и имя для файла решения.

 /project `ProjName` Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.

 /projectconfig `ProjConfigName` Необязательный. Имя конфигурации сборки проекта, которая применяется к указанному `/project`.

## <a name="remarks"></a>Remarks

- Следует использовать в составе команды `devenv /build`, /`clean`, `/rebuild` или `/deploy`.

- Строки с пробелами заключаются в двойные кавычки.

- Сводные данные о сборках, включая ошибки, могут отображаться в **командном** окне или в любом файле журнала, указанном с помощью `/out` параметра.

## <a name="example"></a>Пример
 В этом примере выполняется сборка проекта `CSharpConsoleApp` с использованием конфигурации проекта `Debug` в пределах конфигурация решения `Debug` для `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>См. также:
 [Параметры командной строки devenv](../../ide/reference/devenv-command-line-switches.md) [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/REBUILD (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
