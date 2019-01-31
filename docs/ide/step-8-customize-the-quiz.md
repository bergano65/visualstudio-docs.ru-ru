---
title: Шаг 8. Настройка теста
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aab5e24d046e3b81b507be558f667583fed0ae1e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55022499"
---
# <a name="step-8-customize-the-quiz"></a>Шаг 8. Настройка теста
В последней части этого руководства рассматривается несколько способов изменения викторины и приводятся дополнительные сведения по уже изученным вами вопросам. Например, можно подумать, как программа создает случайные задачи на деление, для которых ответ никогда не будет дробью. В качестве дополнительного занятия измените цвет элемента управления `timeLabel` и дайте игроку викторины подсказку.

## <a name="to-customize-the-quiz"></a>Настройка викторины

-   Когда для решения викторины останется лишь 5 секунд, измените цвет элемента управления **timeLabe** на красный путем задания свойства **BackColor** этого элемента управления (`timeLabel.BackColor = Color.Red;`). Восстановите цвет при завершении игры.

-   Дайте игроку подсказку с помощью воспроизведения звука при вводе правильного ответа в элементе управления <xref:System.Windows.Forms.NumericUpDown>. (Необходимо написать обработчик событий для каждого события <xref:System.Windows.Forms.NumericUpDown.ValueChanged> элемента управления , который срабатывает при каждом изменении игроком значения элемента управления).

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

-   Скачать готовую версию головоломки можно на странице с [полным примером руководства по созданию математической головоломки](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

-   Следующее руководство см. в разделе [ Руководство 3. Создание игры "Подбери пару!"](../ide/tutorial-3-create-a-matching-game.md).

-   Предыдущий раздел руководства: [Шаг 7. Добавление задач на умножение и деление](../ide/step-7-add-multiplication-and-division-problems.md).
