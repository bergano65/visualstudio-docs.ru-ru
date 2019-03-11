---
title: Инверсия инструкции if
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a6dd0a3ebdb41243734850cea4f4b43604ebb94b
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324669"
---
# <a name="invert-if-statement"></a>Инверсия инструкции if

Область применения этого рефакторинга:

- C#
- Visual Basic

**Что?** Позволяет инвертировать инструкцию `if` или `if else`, не изменяя значение кода.

**Когда?** При наличии инструкции `if` или `if else`, которая будет понятнее после инверсии.

**Зачем?** Инверсия инструкции `if` или `if else` вручную может занять гораздо больше времени и привести к ошибкам. Это исправление кода помогает выполнять рефакторинг автоматически.

## <a name="invert-if-statement-refactoring"></a>Рефакторинг "Инверсия инструкции if"

1. Поместите курсор в инструкции `if` или `if else`.

    ![Инверсия if else](media/invert-if.png)

2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.

    ![Исправление "Инверсия if else"](media/invert-if-codefix.png)

3. Выберите **Инвертировать if**.

    ![Результат инверсии if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Советы для разработчиков .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
