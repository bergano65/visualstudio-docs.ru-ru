---
title: -Diff (devenv.exe)
description: Узнайте, как использовать параметр командной строки Diff devenv для сравнения двух файлов.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b1a8c4c8868de187b9e9aa5183e44c29145220e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882151"
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

## <a name="remarks"></a>Комментарии

Если экземпляр интегрированной среды разработки уже открыт, сравниваемые файлы появятся на вкладке в текущей среде.

## <a name="example"></a>Пример

Первый пример сравнивает два файла, не изменяя отображаемые имена. Второй пример сравнивает файлы, изменяя отображаемые имена. Третий и четвертый примеры сравнивают два файла, но применяют псевдоним только к одному из них.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
