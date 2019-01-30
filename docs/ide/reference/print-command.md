---
title: Команда Print
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1677e05668b8681976447ef9ee401624d82bdd9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939833"
---
# <a name="print-command"></a>Команда Print
Вычисляет выражение или отображает указанный текст.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.Print text
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
>? expA
```

 Обе версии этой команды возвращают текущее значение выражения `expA`.

## <a name="example"></a>Пример

```cmd
>Debug.Print varA
```

## <a name="see-also"></a>См. также раздел

- [Команда "Вычислить оператор"](../../ide/reference/evaluate-statement-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)