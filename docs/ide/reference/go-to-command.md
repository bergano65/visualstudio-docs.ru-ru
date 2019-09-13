---
title: Команда Go To
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bdc1c97d35b79fec40bbaf8994176cfbb27b8e8
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919219"
---
# <a name="go-to-command"></a>Команда Go To
Перемещение курсор на указанную строку.

## <a name="syntax"></a>Синтаксис

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Аргументы
`linenumber`\
Необязательный параметр. Целое число, задающее номер строки, к которой нужно перейти.

## <a name="remarks"></a>Примечания
Нумерация строк начинается с единицы. Если значение `linenumber` меньше единицы, отображается первая строка. Если значение `linenumber` больше номера последней строки, отображается последняя строка.

Если значение `linenumber` не указано, отображается диалоговое окно **Переход на строку**.

Эта команда имеет псевдоним GoToLn.

## <a name="example"></a>Пример

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)