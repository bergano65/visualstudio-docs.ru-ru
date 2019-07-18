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
ms.openlocfilehash: 82dd3f226931dfeca2fa0dfad38daa24684fb8da
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789835"
---
# <a name="go-to-command"></a>Команда Go To
Перемещение курсор на указанную строку.

## <a name="syntax"></a>Синтаксис

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Аргументы
 `linenumber`

 Необязательный параметр. Целое число, задающее номер строки, к которой нужно перейти.

## <a name="remarks"></a>Примечания
 Нумерация строк начинается с единицы. Если значение `linenumber` меньше единицы, отображается первая строка. Если значение `linenumber` больше номера последней строки, отображается последняя строка.

 Если значение `linenumber` не указано, отображается диалоговое окно **Переход на строку**.

 Эта команда имеет псевдоним GoToLn.

## <a name="example"></a>Пример

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)