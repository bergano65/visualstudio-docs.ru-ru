---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dfc52c66fd56f2d3d7954584804cfd4e3e75ee24
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227958"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Выполняет указанную команду после запуска интегрированной среды разработки Visual Studio.

## <a name="syntax"></a>Синтаксис

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Аргументы

- *CommandName*

  Обязательный. Полное имя команды Visual Studio или ее псевдоним, заключенные в двойные кавычки. Дополнительные сведения о синтаксисе команд и псевдонимов см. в разделе [Команды Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Примечания

После завершения запуска интегрированная среда разработки выполняет именованную команду. При использовании этого параметра интегрированная среда разработки не отображает начальную страницу Visual Studio при запуске.

Если надстройка предоставляет команду, этот параметр можно использовать для запуска надстройки из командной строки. Дополнительные сведения см. в разделе [Как Управление надстройками с помощью диспетчера надстроек](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Пример

Первый пример запускает Visual Studio и автоматически выполняет макрос Open Favorite Files.

Второй пример открывает вкладку с веб-страницей в интегрированной среде разработки и переходит на сайт документации Майкрософт.

Третий пример создает файл с именем `some_file.cs` и открывает его в редакторе кода.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Командное окно](command-window.md)