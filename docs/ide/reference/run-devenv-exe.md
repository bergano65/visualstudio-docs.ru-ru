---
title: -Run (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e10b12729ed8f547c2658c0f4ce6ece84a12dbe
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704633"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
Компилирует и запускает указанный проект или указанное решение.

## <a name="syntax"></a>Синтаксис

```cmd
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>Аргументы
 `SolutionName`

 Обязательно. Полный путь и имя для файла решения.

 `ProjectName`

 Обязательно. Полный путь и имя для файла проекта.

## <a name="remarks"></a>Примечания
 Компилирует и запускает указанный проект или указанное решение согласно параметрам, заданным для активной конфигурации решения. Этот параметр запускает интегрированную среду разработки (IDE), которая остается активной после завершения выполнения проекта или решения.

-   Строки с пробелами заключаются в двойные кавычки.

-   Сводные данные, включая ошибки, могут отображаться в окне **Команда** или в любом файле журнала, указанном с помощью параметра `/out`.

## <a name="example"></a>Пример
 Этот пример запускает решение `MySolution`, используя активную конфигурацию развертывания.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)