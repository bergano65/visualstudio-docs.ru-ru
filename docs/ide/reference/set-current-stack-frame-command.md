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
ms.openlocfilehash: 314ee2a7dec352f4bcdcf8e7d164950a422b79d2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="set-current-stack-frame-command"></a>Команда Set Current Stack Frame
Позволяет задать определенный кадр стека.

## <a name="syntax"></a>Синтаксис

```
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Аргументы
 `index`

 Обязательно. Выбирает кадр стека по индексу.

## <a name="example"></a>Пример

```
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)