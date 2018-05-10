---
title: Команда Set Current Stack Frame
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 95f8c762f16eb4a784ccc2cffb5bfa27d215370e
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="set-current-stack-frame-command"></a>Команда Set Current Stack Frame
Позволяет задать определенный кадр стека.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Аргументы
 `index`

 Обязательно. Выбирает кадр стека по индексу.

## <a name="example"></a>Пример

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)