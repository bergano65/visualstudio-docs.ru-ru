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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567844"
---
# <a name="print-command"></a>Печать - команда

Вычисляет выражение или отображает указанный текст.

## <a name="syntax"></a>Синтаксис

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Аргументы

`text`

Обязательный элемент. Вычисляемое выражение или отображаемый текст.

## <a name="remarks"></a>Remarks

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

## <a name="see-also"></a>См. также раздел

- [Команда "Вычислить оператор"](../../ide/reference/evaluate-statement-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Окно команд](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
