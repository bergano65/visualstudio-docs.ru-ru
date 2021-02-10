---
title: Команда Toggle Breakpoint
description: Сведения о том, как с помощью команды Toggle Breakpoint включить или отключить точку останова в зависимости от ее текущего состояния и текущей позиции в файле.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0a02cb0659df431b3e6eca7c9ad1f13f8c3676b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886487"
---
# <a name="toggle-breakpoint-command"></a>Команда Toggle Breakpoint
Включает или отключает точку останова в зависимости от ее текущего состояния и текущей позиции в файле.

## <a name="syntax"></a>Синтаксис

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Аргументы

`text`\
Необязательный элемент. Если текст указан, строка помечается как именованная точка останова. В противном случае строка помечается как неименованная точка останова, что аналогично нажатию клавиши F9.

## <a name="example"></a>Пример
В этом примере переключается текущая точка останова.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
