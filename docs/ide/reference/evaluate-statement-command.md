---
title: EvaluateStatement
ms.date: 02/25/2019
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7eff96d1b413ea10b1274eb7d7938148727acbc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790880"
---
# <a name="evaluate-statement-command"></a>Команда Evaluate Statement

Вычисляет и отображает заданный оператор.

## <a name="syntax"></a>Синтаксис

```cmd
>Debug.EvaluateStatement text
```

## <a name="arguments"></a>Аргументы

`text`

Обязательный. Вычисляемый оператор.

## <a name="example"></a>Пример

```cmd
>Debug.EvaluateStatement args.Length
```

## <a name="see-also"></a>См. также

- [Команда "Печать"](../../ide/reference/print-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)