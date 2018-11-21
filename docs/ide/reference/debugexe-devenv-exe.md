---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1badcaba6f6461f6a2c6b73580d8d12c50481c2b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948781"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Открывает указанный исполняемый файл для отладки.

## <a name="syntax"></a>Синтаксис

```cmd
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Аргументы
 `ExecutableFile`

 Обязательно. Путь и имя EXE-файла.

 Если EXE-файл не найден или не существует, никакие предупреждения или ошибки не выводятся, а [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запускается обычным образом.

## <a name="remarks"></a>Примечания
 Строки, следующие за параметром `ExecutableFile`, передаются в этот файл в качестве аргументов.

## <a name="example"></a>Пример
 Следующий пример открывает файл `MyApplication.exe` для отладки.

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)