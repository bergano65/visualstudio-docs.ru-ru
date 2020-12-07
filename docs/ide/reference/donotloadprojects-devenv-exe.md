---
title: -DoNotLoadProjects (devenv.exe)
description: Узнайте, как использовать параметр командной строки DoNotLoadProjects devenv, чтобы открыть указанное решение без загрузки каких-либо проектов.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ef3502a2180f7ae7ed5963deb14844b46f3dbff9
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040632"
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

## <a name="see-also"></a>См. также раздел

- [Фильтрация решений в Visual Studio](../filtered-solutions.md)
- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
