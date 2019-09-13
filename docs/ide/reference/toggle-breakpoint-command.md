---
title: Команда Toggle Breakpoint
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18473fbd8ee0f7c4b415880da61c86de0bae6fc5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925975"
---
# <a name="toggle-breakpoint-command"></a>Команда Toggle Breakpoint
Включает или отключает точку останова в зависимости от ее текущего состояния и текущей позиции в файле.

## <a name="syntax"></a>Синтаксис

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Аргументы

`text`\
Необязательный параметр. Если текст указан, строка помечается как именованная точка останова. В противном случае строка помечается как неименованная точка останова, что аналогично нажатию клавиши F9.

## <a name="example"></a>Пример
В этом примере переключается текущая точка останова.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)