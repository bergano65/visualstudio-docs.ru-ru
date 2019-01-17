---
title: Команда Evaluate Statement
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0be6e57c0c741420006d20c0945b9b8c8b77d51
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864129"
---
# <a name="evaluate-statement-command"></a>Команда Evaluate Statement
Вычисляет и отображает заданный оператор.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Аргументы
 `text` Обязательный. Вычисляемый оператор.

## <a name="remarks"></a>Примечания
 Окно, используемое для ввода команды **EvaluateStatement**, определяет, интерпретируется ли знак равенства (=) как оператор сравнения или оператор присваивания.

 В **командном окне** знак равенства (=) интерпретируется как оператор сравнения. Например, если значения переменных `a` и `b` различаются, то команда

```cmd
>Debug.EvaluateStatement(a=b)
```

 возвращает значение `false`.

 В окне **интерпретации**, напротив, знак равенства (=) интерпретируется как оператор присваивания. Таким образом, команда

```cmd
>Debug.EvaluateStatement(a=b)
```

 присвоит переменной `a` значение переменной `b`.

## <a name="example"></a>Пример

```cmd
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>См. также раздел

- [Команда "Печать"](../../ide/reference/print-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)