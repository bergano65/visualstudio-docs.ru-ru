---
title: Команда Start
description: Сведения о команде Start и о том, как с ее помощью начать отладку запускаемого проекта.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0cae9d4630a854bc24c952380a1e27cbab42d261
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938659"
---
# <a name="start-command"></a>Команда Start
Начинает отладку запускаемого проекта.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Аргументы
`address`

Необязательный элемент. Адрес, по которому программа приостанавливает выполнение, сходен с точкой останова в исходном коде. Этот аргумент применяется только в режиме отладки.

## <a name="remarks"></a>Remarks
При запуске команды **Запустить** она выполняет операцию RunToCursor по указанному адресу.

## <a name="example"></a>Пример
Этот пример запускает отладчик и игнорирует все возникающие исключения.

```cmd
>Debug.Start
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
