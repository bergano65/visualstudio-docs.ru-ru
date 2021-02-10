---
title: Команда List Call Stack
description: Узнайте о команде List Call Stack и о том, как она позволяет отобразить текущий стек вызовов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccb55b1c00621f6e97c8f1297e2cedf2abebe73b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852106"
---
# <a name="list-call-stack-command"></a>Команда List Call Stack
Отображает текущий стек вызовов.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Аргументы

`index`\
Необязательный элемент. Задает текущий кадр стека и не отображает выходные данные.

## <a name="switches"></a>Коммутаторы
Каждый переключатель можно вызвать с помощью его полной или краткой формы.

/Count:`number` [или] /C:`number`

Необязательный параметр. Максимальное количество отображаемых стеков вызова. По умолчанию это значение не ограничено.

/ShowTypes:`yes`|`no` [или] /T:`yes`|`no`

Необязательный параметр. Указывает, отображать или нет типы параметров. Значение по умолчанию — `yes`.

/ShowNames:`yes`|`no` [или] /N:`yes`|`no`

Необязательный параметр. Указывает, отображать или нет имена параметров. Значение по умолчанию — `yes`.

/ShowValues:`yes`|`no` [или] /V:`yes`|`no`

Необязательный параметр. Указывает, отображать или нет значения параметров. Значение по умолчанию — `yes`.

/ShowModule:`yes`|`no` [или] /M:`yes`|`no`

Необязательный параметр. Указывает, отображать или нет имя модуля. Значение по умолчанию — `yes`.

/ShowLineOffset:`yes`|`no` [или] /#:`yes`|`no`

Необязательный параметр. Указывает, отображать или нет смещение строки. Значение по умолчанию — `no`.

/ShowByteOffset:`yes`|`no` [или] /B:`yes`|`no`

Необязательный параметр. Указывает, отображать или нет байтовое смещение. Значение по умолчанию — `no`.

/ShowLanguage:`yes`|`no` [или] /L:`yes`|`no`

Необязательный параметр. Указывает, отображать или нет используемый язык. Значение по умолчанию — `no`.

/IncludeCallsAcrossThreads:`yes`|`no` [или] /I:`yes`|`no`

Необязательный параметр. Указывает, включать или нет вызовы в другие потоки или из других потоков. Значение по умолчанию — `no`.

/ShowExternalCode:`yes`|`no`

Необязательный параметр. Указывает, отображать или нет режим "Только мой код" для стека вызова. Если режим "Только мой код" выключен, отображается весь код, написанный не этим пользователем. Если режим "Только мой код" включен, то код, написанный не этим пользователем, отображается в выходных данных стека вызова как `[external]`.

Thread:`n`

Необязательный параметр. Отображает стек вызова для потока `n`. Если поток не указан, отображается стек вызова для текущего потока.

## <a name="remarks"></a>Комментарии
Изменения аргументов или переключателей применяются при последующих вызовах данной команды. При выполнении самой команды Debug.ListCallStackby отображается весь стек вызова. При указании индекса, например,

```cmd
Debug.ListCallStack 2
```

текущий кадр стека устанавливается на этот кадр (в данном случае на второй).

Для вызова этой команды можно также использовать ее стандартный псевдоним "kb". Например, можно ввести

```cmd
kb 2
```

для установки текущего кадра стека на второй кадр.

## <a name="example"></a>Пример

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>См. также раздел

- [Команда "Вывести дизассемблированный код"](../../ide/reference/list-disassembly-command.md)
- [Команда "Вывести потоки"](../../ide/reference/list-threads-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)