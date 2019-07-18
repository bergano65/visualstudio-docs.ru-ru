---
title: Команда List Threads
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44c66eab323f42ba3aa5392fed657e3afd3a6e5c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946834"
---
# <a name="list-threads-command"></a>Команда List Threads
Отображает список потоков в текущей программе.

## <a name="syntax"></a>Синтаксис

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Аргументы
 `index`

 Необязательный параметр. Выбирает по индексу поток для использования в качестве текущего.

## <a name="remarks"></a>Примечания
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