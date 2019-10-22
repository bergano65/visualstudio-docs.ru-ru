---
title: Команда "Вывести регистры" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3476244d3044eb80dbfce3559479421b012cc5fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659502"
---
# <a name="list-registers-command"></a>Команда List Registers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает значение выбранных регистров и позволяет изменить список отображаемых регистров.

## <a name="syntax"></a>Синтаксис

```
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Переключатели
 /Дисплай [{`register`&#124; `registerGroup`}...] Отображает значения указанного `register` или `registerGroup`. Если `register` или `registerGroup` не задан, отображается список регистров по умолчанию. Аналогичное поведение применяется при отсутствии заданных параметров. Пример:

 `Debug.ListRegisters /Display eax`

 эквивалентно

 `Debug.ListRegisters eax`

 /List отображает все группы регистров в списке.

 /Ватч [{`register`&#124; `registerGroup`}...] Добавляет одно или несколько `register` или `registerGroup` значений в список.

 /Унватч [{`register`&#124; `registerGroup`}...] Удаляет одно или несколько `register` или `registerGroup` значений из списка.

## <a name="remarks"></a>Заметки
 Вместо `Debug.ListRegisters` можно использовать псевдоним `r`.

## <a name="example"></a>Пример
 Этот пример использует псевдоним `r` для `Debug.ListRegisters`, чтобы отобразить значения группы регистров `Flags`.

```
r /Display Flags
```

## <a name="see-also"></a>См. также раздел
 [Основные сведения об отладке](../../debugger/debugging-basics-registers-window.md) [команд Visual Studio](../../ide/reference/visual-studio-commands.md) : окно "регистрация" [как использовать окно "регистры](../../debugger/how-to-use-the-registers-window.md) "
