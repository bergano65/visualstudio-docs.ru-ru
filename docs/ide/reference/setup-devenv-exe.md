---
title: Параметр setup для devenv.exe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3f1f801d4da451d9357082359a1cf001915e1041
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829278"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

Параметр /Setup заставляет Visual Studio выполнять слияние метаданных ресурсов, описывающих меню, панели инструментов и группы команд, из всех доступных пакетов VSPackage.

## <a name="syntax"></a>Синтаксис

```shell
devenv /setup
```

## <a name="remarks"></a>Примечания

У этого параметра нет аргументов. Команда `devenv /setup` обычно выдается в качестве последнего этапа процесса установки. Использование параметра `/setup` не приводит к запуску Visual Studio.

> [!NOTE]
> Для использования параметра `/setup` нужно запустить `devenv` от имени администратора.

## <a name="example"></a>Пример

В этом примере показан последний этап установки версии Visual Studio, включающей пакеты VSPackage.

```shell
devenv /setup
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)