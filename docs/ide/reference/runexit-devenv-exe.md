---
title: -RunExit (devenv.exe)
ms.date: 12/10/2018
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
ms.openlocfilehash: 3fa010e72267dadfb1974f7ce8be3b6b9a3e1cff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935051"
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