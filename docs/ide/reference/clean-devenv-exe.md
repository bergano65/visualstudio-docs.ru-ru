---
title: -Clean (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7827f11a93e517f81eb03cfe2e33305859b4d78
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948859"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
Удаляет все промежуточные файлы и выходные каталоги.

## <a name="syntax"></a>Синтаксис

```
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]
```

## <a name="arguments"></a>Аргументы
 `FileName`

 Обязательно. Полный путь и имя для файла решения или файла проекта.

 /project `ProjName`

 Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.

 /projectconfig `ProjConfigName`

 Необязательный. Имя конфигурации сборки проекта, которая применяется при очистке указанного `/project`.

## <a name="remarks"></a>Примечания
 Этот параметр выполняет те же функции, что и команда меню **Очистить решение** в интегрированной среде разработки (IDE).

 Строки с пробелами заключаются в двойные кавычки.

 Сводные данные для удаления и сборки, включая ошибки, могут отображаться в окне **Команда** или любом файле журнала, указанном с помощью параметра `/out`.

## <a name="example"></a>Пример
 Первый пример очищает решение `MySolution` с использованием конфигурации по умолчанию, указанной в файле решения.

 Второй пример очищает проект `CSharpConsoleApp` с использованием конфигурации сборки проекта `Debug` в пределах конфигурация решения `Debug` для `MySolution`.

```
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean

devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)