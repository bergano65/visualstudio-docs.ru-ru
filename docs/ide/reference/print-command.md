---
title: Команда Print
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cf241ec0a9ff849b52761a241e84a15d287bb88
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="print-command"></a>Команда Print
Вычисляет выражение или отображает указанный текст.

## <a name="syntax"></a>Синтаксис

```
Debug.Print text
```

## <a name="arguments"></a>Аргументы
 `text`

 Обязательно. Вычисляемое выражение или отображаемый текст.

## <a name="remarks"></a>Примечания
 Вы можете использовать вопросительный знак (?) в качестве псевдонима для этой команды. Таким образом, команда

```
>Debug.Print expA
```

 может быть записана в виде

```
>? expA
```

 Обе версии этой команды возвращают текущее значение выражения `expA`.

## <a name="example"></a>Пример

```
>Debug.Print varA
```

## <a name="see-also"></a>См. также

- [Команда "Вычислить оператор"](../../ide/reference/evaluate-statement-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)