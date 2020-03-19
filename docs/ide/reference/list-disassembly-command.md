---
title: Команда List Disassembly
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaeab2e65088b8f1bfce3a6a12f8cd66c3245b75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747922"
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

Необязательный параметр. Указывает, следует ли отображать байты кода. Значение по умолчанию: `no`.

/source:`yes`&#124;`no` [или] /s:`yes`&#124;`no`

Необязательный параметр. Указывает, следует ли отображать исходный код. Значение по умолчанию: `no`.

/symbolnames:`yes`&#124;`no` [или] /names:`yes`&#124;`no` [или] /n:`yes`&#124;`no`

Необязательный параметр. Указывает, следует ли отображать имена символов. Значение по умолчанию: `yes`.

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
- [Окно команд](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)