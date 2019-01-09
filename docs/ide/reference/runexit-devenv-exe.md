---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fa715c97310edc447610b0c0ae61226ab5334f9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955124"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Компилирует и запускает указанный проект или указанное решение, а затем закрывает интегрированную среду разработки (IDE).

## <a name="syntax"></a>Синтаксис

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Аргументы
 `SolutionName`

 Обязательный. Полный путь и имя для файла решения.

 `ProjectName`

 Обязательный. Полный путь и имя для файла проекта.

## <a name="remarks"></a>Примечания
 Компилирует и запускает указанный проект или указанное решение согласно параметрам, заданным для активной конфигурации решения. Этот параметр свертывает интегрированную среду разработки во время выполнения проекта или решения и закрывает ее их завершения.

-   Строки с пробелами заключаются в двойные кавычки.

-   Сводные данные, включая ошибки, могут отображаться в окне **Команда** или в любом файле журнала, указанном с помощью параметра `/out`.

## <a name="example"></a>Пример
 Этот пример запускает решение `MySolution` в свернутой интегрированной среде разработки, используя активную конфигурацию развертывания, а затем закрывает эту среду.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)