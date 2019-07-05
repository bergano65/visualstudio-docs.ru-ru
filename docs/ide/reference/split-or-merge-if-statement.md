---
title: Разбиение и объединение операторов If
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 405ccd4bc0197ce06aa14982a16dc02f6d13a537
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160740"
---
# <a name="split-or-merge-if-statements"></a>Разбиение и объединение операторов If

Область применения этого рефакторинга:

- C#

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