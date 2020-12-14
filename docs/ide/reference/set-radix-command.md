---
title: Команда Set Radix
description: Сведения о команде Set Radix и о том, как с ее помощью задать или вернуть числовой базовый тип, используемый для отображения целочисленных значений.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b47c30ed938a83a2b4c47f73f55b5f7ca1db6a62
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616412"
---
# <a name="set-radix-command"></a>Команда Set Radix
Задает или возвращает числовой базовый тип, используемый для отображения целочисленных значений.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Аргументы
`10` или `16` или `hex` или `dec`

Необязательный элемент. Указывает десятичную (10 или dec) или шестнадцатеричную (16 или hex) систему счисления. Если аргумент отсутствует, возвращается основание текущей системы счисления.

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