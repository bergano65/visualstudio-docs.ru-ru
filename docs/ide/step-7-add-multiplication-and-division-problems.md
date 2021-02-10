---
title: Шаг 7. Добавление задач на умножение и деление
description: Узнайте, как добавлять задачи на умножение и деление.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 20d39f6694f0e5a05a220206d8d34ad3bb65946a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868872"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Шаг 7. Добавление задач на умножение и деление

В седьмой части этого учебника вам предстоит добавить задачи на умножение и деление. Сначала, однако, необходимо подумать, как внести это изменение. Рассмотрим начальный шаг, который предполагает сохранение значений.

> [!NOTE]
> Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-multiplication-and-division-problems"></a>Добавление задач на умножение и деление

1. Добавьте в форму еще четыре целочисленные переменные.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Как вы делали раньше, внесите изменения в метод `StartTheQuiz()`, чтобы он подставлял случайные числа для задач на умножение и деление.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Измените метод `CheckTheAnswer()` таким образом, чтобы он также проверял задачи на умножение и деление.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Так как простого способа ввести знак умножения (×) и знак деления (÷) с клавиатуры нет, в языках C# и Visual Basic используется знак звездочка (*) для умножения и знак косой черты (/) для деления.

4. Измените последнюю часть обработчика событий таймера <xref:System.Windows.Forms.Timer.Tick> так, чтобы по истечении времени этот обработчик событий выдавал правильный ответ.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Сохраните и выполните программу.

     Игроки должны решить четыре задачи, чтобы пройти головоломку, как показано на следующем рисунке.

     ![Математическая головоломка с четырьмя задачами](../ide/media/express_finishedquiz.png)<br/>
***Математическая головоломка** _ _с четырьмя задачами*

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: **[Шаг 8. Настройка теста](../ide/step-8-customize-the-quiz.md)** .

- Предыдущий раздел: [Шаг 6. Добавление задачи на вычитание](../ide/step-6-add-a-subtraction-problem.md).
