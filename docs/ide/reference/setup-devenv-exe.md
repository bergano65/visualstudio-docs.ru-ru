---
title: Параметр setup для devenv.exe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f3d78ebb63434df38735bdf24e9d4fcba8f172c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
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

- [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)