---
title: Команда List Registers
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1113f7a4e1a61e6fe2954dfe8d98b9b2c52e6732
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="list-registers-command"></a>Команда List Registers
Отображает значение выбранных регистров и позволяет изменить список отображаемых регистров.

## <a name="syntax"></a>Синтаксис

```
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Переключатели
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

## <a name="remarks"></a>Примечания
 Вместо `Debug.ListRegisters` можно использовать псевдоним `r`.

## <a name="example"></a>Пример
 Этот пример использует псевдоним `r` для `Debug.ListRegisters`, чтобы отобразить значения группы регистров `Flags`.

```
r /Display Flags
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Общие сведения об отладке: окно регистров](../../debugger/debugging-basics-registers-window.md)
- [Практическое руководство. Использование окна регистров](../../debugger/how-to-use-the-registers-window.md)