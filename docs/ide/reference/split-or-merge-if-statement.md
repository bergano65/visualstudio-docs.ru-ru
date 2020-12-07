---
title: Разбиение и объединение операторов If
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для разделения или объединения операторов If.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f72c6c2ed1cfdd1c8ea4471976d6a4980dfe422f
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479931"
---
# <a name="split-or-merge-if-statements"></a>Разбиение и объединение операторов If

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** **Что?** Разбиение и объединение инструкций [if](/dotnet/csharp/language-reference/keywords/if-else).

**Когда?** Разделяйте инструкции `if`, которые используют операторы `&&` или `||`, на вложенные инструкции `if` или объединяйте инструкции `if` с внешними инструкциями `if`.

**Зачем?** Это всего лишь вопрос предпочтений.  

## <a name="how-to"></a>Практическое руководство

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

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)