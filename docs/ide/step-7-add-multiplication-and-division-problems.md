---
title: Шаг 7. Добавление задач на умножение и деление
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbeeca2e53addab923fa3f62c661543497ea1f35
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Шаг 7. Добавление задач на умножение и деление
В седьмой части этого учебника вам предстоит добавить задачи на умножение и деление. Сначала, однако, необходимо подумать, как внести это изменение. Рассмотрим начальный шаг, который предполагает сохранение значений.  

### <a name="to-add-multiplication-and-division-problems"></a>Добавление задач на умножение и деление  

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

4.  Измените последнюю часть обработчика событий таймера Tick таким образом, чтобы по истечении времени этот обработчик событий проставлял правильный ответ.  

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]  

5.  Сохраните и выполните программу.  

     Игроки должны решить четыре задачи, чтобы пройти головоломку, как показано на следующем рисунке.  

     ![Математическая головоломка с четырьмя задачами](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
Математическая головоломка с четырьмя задачами  

### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  

-   Следующий шаг руководства см. в разделе [Step 8: Customize the Quiz](../ide/step-8-customize-the-quiz.md) (Шаг 8. Настройка головоломки).  

-   Предыдущий шаг руководства см. в разделе [Step 6: Add a Subtraction Problem](../ide/step-6-add-a-subtraction-problem.md) (Шаг 6. Добавление задачи на вычитание).
