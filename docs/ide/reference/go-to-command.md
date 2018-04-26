---
title: Команда Go To
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b55e399dab41065fb96f9f3ac8e80484860f5187
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="go-to-command"></a>Команда Go To
Перемещение курсор на указанную строку.

## <a name="syntax"></a>Синтаксис

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Аргументы
 `linenumber`

 Необязательный. Целое число, задающее номер строки, к которой нужно перейти.

## <a name="remarks"></a>Примечания
 Нумерация строк начинается с единицы. Если значение `linenumber` меньше единицы, отображается первая строка. Если значение `linenumber` больше номера последней строки, отображается последняя строка.

 Если значение `linenumber` не указано, отображается диалоговое окно **Переход на строку**.

 Эта команда имеет псевдоним GoToLn.

## <a name="example"></a>Пример

```
>Edit.GoTo 125
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)