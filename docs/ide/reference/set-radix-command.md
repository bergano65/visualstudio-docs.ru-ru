---
title: Команда Set Radix
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f920311301b722c11bea4a9f4eb90e9aa7663d80
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747735"
---
# <a name="set-radix-command"></a>Команда Set Radix
Задает или возвращает числовой базовый тип, используемый для отображения целочисленных значений.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Аргументы
`10` или `16` или `hex` или `dec`

Необязательный параметр. Указывает десятичную (10 или dec) или шестнадцатеричную (16 или hex) систему счисления. Если аргумент отсутствует, возвращается основание текущей системы счисления.

## <a name="example"></a>Пример
В приведенном примере в среде настраивается отображение целочисленных значений в шестнадцатеричном формате.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)