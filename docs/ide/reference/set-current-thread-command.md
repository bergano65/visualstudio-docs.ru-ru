---
title: Команда Set Current Thread
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d782a507d57e459aa5735cf34717f13e41d4cde
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748618"
---
# <a name="set-current-thread-command"></a>Команда Set Current Thread
Задает указанный поток в качестве текущего.

## <a name="syntax"></a>Синтаксис

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Аргументы
`index`

Обязательный. Выбирает поток по индексу.

## <a name="example"></a>Пример

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)