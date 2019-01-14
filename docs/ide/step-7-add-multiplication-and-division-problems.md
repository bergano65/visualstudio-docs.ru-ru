---
title: Шаг 7. Добавление задач на умножение и деление
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 359f4e5035c564a3f7f4b117994ab4d84d1f6eff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889005"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Шаг 7. Добавление задач на умножение и деление
В седьмой части этого учебника вам предстоит добавить задачи на умножение и деление. Сначала, однако, необходимо подумать, как внести это изменение. Рассмотрим начальный шаг, который предполагает сохранение значений.

## <a name="to-add-multiplication-and-division-problems"></a>Добавление задач на умножение и деление

1.  Добавьте в форму еще четыре целочисленные переменные.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

2.  Как вы делали раньше, внесите изменения в метод `StartTheQuiz()`, чтобы он подставлял случайные числа для задач на умножение и деление.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3.  Измените метод `CheckTheAnswer()` таким образом, чтобы он также проверял задачи на умножение и деление.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Так как простого способа ввести знак умножения (×) и знак деления (÷) с клавиатуры нет, в языках Visual C# и Visual Basic используется знак звездочка (*) для умножения и знак косой черты (/) для деления.

4.  Измените последнюю часть обработчика событий таймера <xref:System.Windows.Forms.Timer.Tick> так, чтобы по истечении времени этот обработчик событий выдавал правильный ответ.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5.  Сохраните и выполните программу.

     Игроки должны решить четыре задачи, чтобы пройти головоломку, как показано на следующем рисунке.

     ![Math quiz with four problems](../ide/media/express_finishedquiz.png)
**Математическая головоломка** с четырьмя задачами

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

-   Следующий раздел руководства: [Шаг 8. Настройка теста](../ide/step-8-customize-the-quiz.md).

-   Предыдущий раздел руководства: [Шаг 6. Добавление задачи на вычитание](../ide/step-6-add-a-subtraction-problem.md).
