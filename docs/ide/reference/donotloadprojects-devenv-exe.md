---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569859"
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

Обязательный элемент. Полный путь и имя открываемого решения.

## <a name="example"></a>Пример

В этом примере открывается решение MySln.sln без загрузки каких-либо проектов.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>См. также раздел

- [Фильтрация решений в Visual Studio](../filtered-solutions.md)
- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
