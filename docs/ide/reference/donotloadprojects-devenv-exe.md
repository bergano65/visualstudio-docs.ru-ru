---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a414fde4dee401016e997fa5d6890da2ae8d9d53
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083931"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Новые возможности в Visual Studio 2019 версии 16.1**

Открывает указанное решение без загрузки каких-либо проектов. Дополнительные сведения см. в статье [Фильтрация решений в Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Синтаксис

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Аргументы

*SolutionName*

Обязательный. Полный путь и имя открываемого решения.

## <a name="example"></a>Пример

В этом примере открывается решение MySln.sln без загрузки каких-либо проектов.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>См. также

- [Фильтрация решений в Visual Studio](../filtered-solutions.md)
- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
