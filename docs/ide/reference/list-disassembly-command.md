---
title: Команда List Disassembly
description: Узнайте о команде List Disassembly и о том, как она начинает процесс отладки и позволяет указать способ обработки ошибок.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0de7becc46205e5fb8865a0419102bf65afde14e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852093"
---
# <a name="list-disassembly-command"></a>Команда List Disassembly
Начинает процесс отладки и позволяет указать способ обработки ошибок.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Коммутаторы
Каждый переключатель можно вызвать с помощью его полной или краткой формы.

/count: `number` [или] /c: `number` [или] /length: `number` [или] /l: `number`

Необязательный параметр. Количество инструкций для отображения. Значение по умолчанию — 8.

/endaddress: `expression` [или] /e: `expression`

Необязательный параметр. Адрес, на котором нужно остановить дизассемблирование.

/codebytes:`yes`&#124;`no` [или] /bytes:`yes`&#124;`no` [или] /b:`yes`&#124;`no`

Необязательный параметр. Указывает, следует ли отображать байты кода. Значение по умолчанию — `no`.

/source:`yes`&#124;`no` [или] /s:`yes`&#124;`no`

Необязательный параметр. Указывает, следует ли отображать исходный код. Значение по умолчанию — `no`.

/symbolnames:`yes`&#124;`no` [или] /names:`yes`&#124;`no` [или] /n:`yes`&#124;`no`

Необязательный параметр. Указывает, следует ли отображать имена символов. Значение по умолчанию — `yes`.

 [/linenumbers:`yes`&#124;`no`]

Необязательный параметр. Включает просмотр номеров строк, связанных с исходным кодом. Параметр/source должен иметь значение `yes`, чтобы можно было использовать параметр /linenumbers.

## <a name="example"></a>Пример

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>См. также раздел

- [Команда "Вывести стек вызовов"](../../ide/reference/list-call-stack-command.md)
- [Команда "Вывести потоки"](../../ide/reference/list-threads-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)