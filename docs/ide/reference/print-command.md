---
title: Debug.Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae87afb11be71af8f0582a0b2899d67ba970186e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747827"
---
# <a name="print-command"></a>Команда Print

Вычисляет выражение или отображает указанный текст.

## <a name="syntax"></a>Синтаксис

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Аргументы

`text`

Обязательный. Вычисляемое выражение или отображаемый текст.

## <a name="remarks"></a>Примечания

Вы можете использовать вопросительный знак (?) в качестве псевдонима для этой команды. Таким образом, команда

```cmd
>Debug.Print expA
```

может быть записана в виде

```cmd
? expA
```

Обе версии этой команды возвращают текущее значение выражения `expA`.

## <a name="example"></a>Пример

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>См. также

- [Команда "Вычислить оператор"](../../ide/reference/evaluate-statement-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)