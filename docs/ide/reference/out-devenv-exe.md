---
title: -Out (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 039456c10993199ec2265042aabc0ed5c475ccd9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954742"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Определяет файл для хранения и отображения ошибок при [запуске](run-devenv-exe.md), [запуске и выполнении](runexit-devenv-exe.md), [обновлении](upgrade-devenv-exe.md), [сборке](build-devenv-exe.md), [повторной сборке](rebuild-devenv-exe.md), [очистке](clean-devenv-exe.md) или [повторном развертывании](deploy-devenv-exe.md) решения.

## <a name="syntax"></a>Синтаксис

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Аргументы

- *FileName*

  Обязательный. Путь и имя файла для приема выходных данных при сборке исполняемого файла.

## <a name="remarks"></a>Примечания

Если указано имя несуществующего файла, такой файл создается автоматически. Если файл уже существует, результаты добавляются к имеющемуся в нем содержимому.

Ошибки сборки в командной строке отображаются в окне **Команда** и представлении построителя решений в окне **Вывод**. Этот параметр полезен для просмотра результатов автоматических сборок.

## <a name="example"></a>Пример

Этот пример запускает `MySolution` и записывает ошибки в файл `MyErrorLog.txt`.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)