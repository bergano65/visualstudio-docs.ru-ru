---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4eb1eb49cd6b29740fb6d365a98a51cc28387e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661669"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Открывает указанный исполняемый файл для отладки.

## <a name="syntax"></a>Синтаксис

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Аргументы

- *ExecutableFile*

  Обязательный. Путь и имя файла `.exe`. Если файл `.exe` не найден или не существует, предупреждения или ошибки не выводятся, а Visual Studio запускается обычным образом.

## <a name="remarks"></a>Примечания

Строки, следующие за параметром *ExecutableFile*, передаются в этот файл в качестве аргументов.

## <a name="example"></a>Пример

Следующий пример открывает файл `MyApplication.exe` для отладки.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)