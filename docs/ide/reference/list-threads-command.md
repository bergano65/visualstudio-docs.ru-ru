---
title: Команда List Threads
description: Узнайте о команде List Threads и о том, как использовать ее для отображения списка потоков в текущей программе.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3abcd7182c8bb5b94b2f35a9463f845cc6bb5bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919380"
---
# <a name="list-threads-command"></a>Команда List Threads
Отображает список потоков в текущей программе.

## <a name="syntax"></a>Синтаксис

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Аргументы
`index`

Необязательный элемент. Выбирает по индексу поток для использования в качестве текущего.

## <a name="remarks"></a>Комментарии
Если параметр указан, аргумент `index` помечает указанный поток в качестве текущего. Рядом с текущим потоком в списке отображается звездочка (*).

## <a name="example"></a>Пример

```
>Debug.ListThreads
```

## <a name="see-also"></a>См. также раздел

- [Команда "Вывести стек вызовов"](../../ide/reference/list-call-stack-command.md)
- [Команда "Вывести дизассемблированный код"](../../ide/reference/list-disassembly-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
