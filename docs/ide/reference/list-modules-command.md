---
title: Команда List Modules
description: Узнайте о команде List Modules и о том, как она позволяет получить список модулей для текущего процесса.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa0c3f6445a22ee80457e8a7f9f24fb7008f77ed
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305309"
---
# <a name="list-modules-command"></a>Команда List Modules
Отображает список модулей для текущего процесса.

## <a name="syntax"></a>Синтаксис

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Параметры
/Address:`yes|no`

Необязательный параметр. Указывает, нужно ли отображать адреса модулей в памяти. Значение по умолчанию — `yes`.

/Name:`yes|no`

Необязательный параметр. Указывает, нужно ли отображать имена модулей. Значение по умолчанию — `yes`.

/Order:`yes|no`

Необязательный параметр. Указывает, нужно ли отображать порядок модулей. Значение по умолчанию — `no`.

/Path:`yes|no`

Необязательный параметр. Указывает, нужно ли отображать пути к модулям. Значение по умолчанию — `yes`.

/Process:`yes|no`

Необязательный параметр. Указывает, нужно ли отображать процессы модулей. Значение по умолчанию — `no`.

/SymbolFile:`yes|no`

Необязательный параметр. Указывает, нужно ли отображать файлы символов модулей. Значение по умолчанию — `no`.

/SymbolStatus:`yes|no`

Необязательный параметр. Указывает, нужно ли отображать состояния символов модулей. Значение по умолчанию — `yes`.

/Timestamp:`yes|no`

Необязательный параметр. Указывает, нужно ли отображать метки времени модулей. Значение по умолчанию — `no`.

/Version:`yes|no`

Необязательный параметр. Указывает, нужно ли отображать версии модулей. Значение по умолчанию — `no`.

## <a name="example"></a>Пример
В этом примере демонстрируется создание списка имен модулей для текущего процесса с указанием адресов и меток времени.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Практическое руководство. Использование окна модулей](../../debugger/how-to-use-the-modules-window.md)
