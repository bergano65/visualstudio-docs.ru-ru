---
title: команда «Перейти к»
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 535906d8b8d7f8ba0c2984d22ceead18a0d47c2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569209"
---
# <a name="go-to-command"></a>команда «Перейти к»
Перемещение курсор на указанную строку.

## <a name="syntax"></a>Синтаксис

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Аргументы
`linenumber`\
Необязательный параметр. Целое число, задающее номер строки, к которой нужно перейти.

## <a name="remarks"></a>Remarks
Нумерация строк начинается с единицы. Если значение `linenumber` меньше единицы, отображается первая строка. Если значение `linenumber` больше номера последней строки, отображается последняя строка.

Если значение `linenumber` не указано, отображается диалоговое окно **Переход на строку**.

Эта команда имеет псевдоним GoToLn.

## <a name="example"></a>Пример

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Окно команд](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
