---
title: -DebugExe (devenv.exe)
description: Узнайте, как использовать параметр командной строки DebugExe devenv, чтобы открыть указанный исполняемый файл для отладки.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e60c3fb8a72caa44bcf70ac36850748ce240d42
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039475"
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

## <a name="remarks"></a>Комментарии

Строки, следующие за параметром *ExecutableFile*, передаются в этот файл в качестве аргументов.

## <a name="example"></a>Пример

Следующий пример открывает файл `MyApplication.exe` для отладки.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
