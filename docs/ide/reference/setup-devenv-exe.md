---
title: Параметр devenv.exe | Документы Майкрософт
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: eee6e30a7489f5097cb17a19513c2a423187c827
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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

[Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)