---
title: Команда Start
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6138c4cff33f0b2a4211439a01a058da59da811
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590284"
---
# <a name="start-command"></a>Команда Start
Начинает отладку запускаемого проекта.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Аргументы
`address`

Необязательный параметр. Адрес, по которому программа приостанавливает выполнение, сходен с точкой останова в исходном коде. Этот аргумент применяется только в режиме отладки.

## <a name="remarks"></a>Remarks
При запуске команды **Запустить** она выполняет операцию RunToCursor по указанному адресу.

## <a name="example"></a>Пример
Этот пример запускает отладчик и игнорирует все возникающие исключения.

```cmd
>Debug.Start
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Окно команд](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
