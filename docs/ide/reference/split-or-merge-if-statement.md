---
title: Разбиение и объединение операторов If
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a3b42f83faacda6be34b282150cf4fb4c0f379f1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093664"
---
# <a name="split-or-merge-if-statements"></a>Разбиение и объединение операторов If

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** **Что?** Разбиение и объединение инструкций [if](/dotnet/csharp/language-reference/keywords/if-else).

**Когда?** Разделяйте инструкции `if`, которые используют операторы `&&` или `||`, на вложенные инструкции `if` или объединяйте инструкции `if` с внешними инструкциями `if`.

**Зачем?** Это всего лишь вопрос предпочтений.  

## <a name="how-to"></a>Практические советы

Если вы хотите разделить инструкцию `if`:

1. Поместите курсор в инструкцию `if` рядом с оператором `&&` или `||`.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

    ![Разделение инструкции If](../media/split-if-statement.png)

3. Выберите **Разделить на вложенные инструкции if**.

    ![Разделение инструкции If завершено](../media/split-if-statement-complete.png)

Если вы хотите объединить внутреннюю инструкцию `if` с внешней инструкцией `if`: 

1. Поместите курсор во внутреннее ключевое слово `if`.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

    ![Объединение инструкции If](../media/merge-if-statement.png)

3. Выберите **Объединить с внешней инструкцией if**.

    ![Объединение инструкции If завершено](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)