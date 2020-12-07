---
title: Debug.Print
description: Узнайте о команде Print и также о том, как она позволяет вычислять выражения или отображать указанный текст.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0524ce015ea4675254615c11e5768e59049c37f6
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304126"
---
# <a name="print-command"></a>Печать - команда

Вычисляет выражение или отображает указанный текст.

## <a name="syntax"></a>Синтаксис

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Аргументы

`text`

Обязательный. Вычисляемое выражение или отображаемый текст.

## <a name="remarks"></a>Комментарии

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
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
