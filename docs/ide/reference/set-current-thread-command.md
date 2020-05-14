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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
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

Обязательный элемент. Выбирает поток по индексу.

## <a name="example"></a>Пример

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Окно команд](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)