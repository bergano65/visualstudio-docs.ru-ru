---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d438e9cea35cbf178658d8def78e264804240c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654513"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Сравнение двух файлов. Различия отображаются в специальном окне Visual Studio.

## <a name="syntax"></a>Синтаксис

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Аргументы

- *SourceFile*

  Обязательный. Полный путь и имя первого файла, который следует сравнить.

- *TargetFile*

  Обязательный. Полный путь и имя второго сравниваемого файла.

- *SourceDisplayName*

  Необязательный параметр. Отображаемое имя первого файла.

- *TargetDisplayName*

  Необязательный параметр. Отображаемое имя второго файла.

## <a name="remarks"></a>Примечания

Если экземпляр интегрированной среды разработки уже открыт, сравниваемые файлы появятся на вкладке в текущей среде.

## <a name="example"></a>Пример

Первый пример сравнивает два файла, не изменяя отображаемые имена. Второй пример сравнивает файлы, изменяя отображаемые имена. Третий и четвертый примеры сравнивают два файла, но применяют псевдоним только к одному из них.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
