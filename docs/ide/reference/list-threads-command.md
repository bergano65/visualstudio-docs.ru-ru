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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1b36b8f4d9970d94eb83c47b59e85d01f932589
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595492"
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

## <a name="remarks"></a>Примечания
Если параметр указан, аргумент `index` помечает указанный поток в качестве текущего. Рядом с текущим потоком в списке отображается звездочка (*).

## <a name="example"></a>Пример

```
>Debug.ListThreads
```

## <a name="see-also"></a>См. также

- [Команда "Вывести стек вызовов"](../../ide/reference/list-call-stack-command.md)
- [Команда "Вывести дизассемблированный код"](../../ide/reference/list-disassembly-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
