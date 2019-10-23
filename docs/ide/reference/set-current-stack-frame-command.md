---
title: Команда Set Current Stack Frame
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 088fe9871b54e69b015ffdc9dcdaf23de3d98e0e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747759"
---
# <a name="set-current-stack-frame-command"></a>Команда Set Current Stack Frame
Позволяет задать определенный кадр стека.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Аргументы
`index`

Обязательный. Выбирает кадр стека по индексу.

## <a name="example"></a>Пример

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)