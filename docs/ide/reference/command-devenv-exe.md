---
title: -Command (devenv.exe)
description: Узнайте, как использовать команду Command devenv с параметром командной строки, чтобы выполнить указанную команду после запуска интегрированной среды разработки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38738dad275b38fe0c5a6a70104e80f6a794bab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882190"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Выполняет указанную команду после запуска интегрированной среды разработки Visual Studio.

## <a name="syntax"></a>Синтаксис

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Аргументы

*CommandName*

Обязательный. Полное имя команды Visual Studio или ее псевдоним, заключенные в двойные кавычки. Дополнительные сведения о синтаксисе команд и псевдонимов см. в разделе [Команды Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Комментарии

После завершения запуска интегрированная среда разработки выполняет именованную команду.

::: moniker range="vs-2017"

При использовании этого параметра среда IDE не отображает начальную страницу при запуске.

::: moniker-end

Если надстройка предоставляет команду, этот параметр можно использовать для запуска надстройки из командной строки. Дополнительные сведения см. в разделе [Практическое руководство. Управление надстройками с помощью диспетчера надстроек](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Пример

Первый пример запускает Visual Studio и автоматически выполняет макрос Open Favorite Files.

Второй пример открывает вкладку с веб-страницей в интегрированной среде разработки и переходит на сайт документации Майкрософт.

Третий пример создает файл с именем `some_file.cs` и открывает его в редакторе кода.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Командное окно](command-window.md)
