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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeae28288936b6723b53e826142a4888ad0bc8b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570145"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Открывает указанный исполняемый файл для отладки.

## <a name="syntax"></a>Синтаксис

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Аргументы

- *ExecutableFile*

  Обязательный элемент. Путь и имя файла `.exe`. Если файл `.exe` не найден или не существует, предупреждения или ошибки не выводятся, а Visual Studio запускается обычным образом.

## <a name="remarks"></a>Remarks

Строки, следующие за параметром *ExecutableFile*, передаются в этот файл в качестве аргументов.

## <a name="example"></a>Пример

Следующий пример открывает файл `MyApplication.exe` для отладки.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
