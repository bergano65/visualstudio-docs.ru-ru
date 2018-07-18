---
title: Команда List Threads
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa44556be7c20c52d44ec83da1ba9d4972b4542d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947434"
---
# <a name="list-threads-command"></a>Команда List Threads
Отображает список потоков в текущей программе.

## <a name="syntax"></a>Синтаксис

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Аргументы
 `index`

 Необязательный. Выбирает по индексу поток для использования в качестве текущего.

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
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)