---
title: -Rebuild (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 008169829a6cf76e959d00f010959239a5f390b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665651"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Удаляет и затем выполняет сборку заданной конфигурации решения.

## <a name="syntax"></a>Синтаксис

```
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Аргументы
 `SolnConfigName` Обязательный. Имя конфигурации решения, которая будет применяться для перестроения решения, указанного в `SolutionName`.

 `SolutionName` Обязательный. Полный путь и имя для файла решения.

 /project `ProjName` Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.

 /projectconfig `ProjConfigName` Необязательный. Имя конфигурации сборки проекта, которая применяется при перестроении указанного `/project`.

## <a name="remarks"></a>Remarks

- Этот параметр выполняет те же функции, что и команда меню **Перестроить решение** в интегрированной среде разработки (IDE).

- Строки с пробелами заключаются в двойные кавычки.

- Сводные данные для удаления и сборки, включая ошибки, могут отображаться в окне **Команда** или любом файле журнала, указанном с помощью параметра `/out`.

## <a name="example"></a>Пример
 В этом примере выполняется удаление и перестроение проекта `CSharpWinApp` с помощью конфигурации сборки `Debug` в конфигурации решения `Debug``MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>См. также:
 [Параметры командной строки devenv](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
