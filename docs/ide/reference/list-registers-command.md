---
title: Команда List Registers
description: Узнайте о команде List Registers и о том, как она отображает значения выбранных регистров и позволяет изменить список отображаемых регистров.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0168f8e4b6c04ea0d6b675ce6c280bd8140971b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919571"
---
# <a name="list-registers-command"></a>Команда List Registers
Отображает значение выбранных регистров и позволяет изменить список отображаемых регистров.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Коммутаторы
/Display [{`register`&#124;`registerGroup`}...]

Отображает значения указанного `register` или `registerGroup`. Если `register` или `registerGroup` не задан, отображается список регистров по умолчанию. Аналогичное поведение применяется при отсутствии заданных параметров. Пример:

`Debug.ListRegisters /Display eax`

эквивалентно

`Debug.ListRegisters eax`

/List

Отображает все группы регистров в списке.

/Watch [{`register`&#124;`registerGroup`}...]

Добавляет одно или несколько значений `register` или `registerGroup` в список.

/Unwatch [{`register`&#124;`registerGroup`}...]

Удаляет одно или несколько значений `register` или `registerGroup` из списка.

## <a name="remarks"></a>Комментарии
Вместо `Debug.ListRegisters` можно использовать псевдоним `r`.

## <a name="example"></a>Пример
Этот пример использует псевдоним `r` для `Debug.ListRegisters`, чтобы отобразить значения группы регистров `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Общие сведения об отладке: окно регистров](../../debugger/debugging-basics-registers-window.md)
- [Практическое руководство. Использование окна регистров](../../debugger/how-to-use-the-registers-window.md)
