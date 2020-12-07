---
title: команда «Перейти к»
description: Узнайте о команде "Перейти к" и о том, как она позволяет переместить курсор в указанную строку.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b0ef161cb8108ed3244c263ee51fee4251fc05d8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305203"
---
# <a name="go-to-command"></a>команда «Перейти к»
Перемещение курсор на указанную строку.

## <a name="syntax"></a>Синтаксис

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Аргументы
`linenumber`\
Необязательный элемент. Целое число, задающее номер строки, к которой нужно перейти.

## <a name="remarks"></a>Комментарии
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
