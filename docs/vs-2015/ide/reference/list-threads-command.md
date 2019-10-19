---
title: Команда "Вывести потоки" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc11479901785b19235e0962d3ae90e552e5b33b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671141"
---
# <a name="list-threads-command"></a>Команда List Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает список потоков в текущей программе.

## <a name="syntax"></a>Синтаксис

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Аргументы
 `index` Необязательный. Выбирает по индексу поток для использования в качестве текущего.

## <a name="remarks"></a>Примечания
 Если параметр указан, аргумент `index` помечает указанный поток в качестве текущего. Рядом с текущим потоком в списке отображается звездочка (*).

## <a name="example"></a>Пример

```
>Debug.ListThreads
```

## <a name="see-also"></a>См. также
 Список [команд стека вызовов](../../ide/reference/list-call-stack-command.md) [Командная поддизассемблированный код команда](../../ide/reference/list-disassembly-command.md) [Visual Studio команды](../../ide/reference/visual-studio-commands.md) [команда](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) Командная команда [Visual Studio псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
