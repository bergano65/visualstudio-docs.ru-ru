---
title: Команда Set Radix
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93172b8ed16e2520c060671d12ef0ab35960f6ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829412"
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

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)