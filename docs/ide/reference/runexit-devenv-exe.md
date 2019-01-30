---
title: -RunExit (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3d426ec4737d2024a4dd24e74753fc216181536
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069817"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Компилирует и запускает указанный проект или указанное решение, а затем закрывает интегрированную среду разработки (IDE).

## <a name="syntax"></a>Синтаксис

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Аргументы

- *SolutionName*

  Полный путь и имя для файла решения.

- *ProjectName*

  Полный путь и имя для файла проекта.

- `/Out` *OutputFilename*

  Необязательный параметр. Имя файла, в который вы хотите отправить выходные данные средства. Если файл уже существует, средство добавляет в его конец выходные данные.

## <a name="remarks"></a>Примечания

Компилирует и запускает указанный проект или указанное решение согласно параметрам, заданным для активной конфигурации решения. Этот параметр свертывает интегрированную среду разработки во время выполнения проекта или решения. Он закрывает интегрированную среду разработки после выполнения проекта или решения.

- Строки с пробелами заключаются в двойные кавычки.

- Сводные данные, включая ошибки, могут отображаться в окне **Команда** или в любом файле журнала, указанном с помощью параметра `/Out`.

## <a name="example"></a>Пример

Этот пример запускает решение `MySolution` в свернутой интегрированной среде разработки, используя активную конфигурацию развертывания, а затем закрывает эту среду.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)