---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 99f256b47125f4e07ca5dc148c4351871389a94b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889414"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Открывает указанный исполняемый файл для отладки.

## <a name="syntax"></a>Синтаксис

```cmd
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Аргументы
 `ExecutableFile`

 Обязательный. Путь и имя EXE-файла.

 Если EXE-файл не найден или не существует, никакие предупреждения или ошибки не выводятся, а [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запускается обычным образом.

## <a name="remarks"></a>Примечания
 Строки, следующие за параметром `ExecutableFile`, передаются в этот файл в качестве аргументов.

## <a name="example"></a>Пример
 Следующий пример открывает файл `MyApplication.exe` для отладки.

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)