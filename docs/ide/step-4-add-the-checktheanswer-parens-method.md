---
title: Шаг 4. Добавление метода CheckTheAnswer()
description: Узнайте, как написать метод CheckTheAnswer(), который проверяет правильность ответов на арифметические задачи.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f6e52d415b4278a04e559c64cdcfac86cdf22261
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950709"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Шаг 4. Добавление метода CheckTheAnswer()

В четвертой части этого урока вам предстоит написать метод `CheckTheAnswer()`, который проверяет правильность ответов на арифметические задачи. Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>Проверка правильности ответов

> [!NOTE]
> Если вы разрабатываете головоломку на Visual Basic, вам необходимо будет использовать ключевое слово `Function` вместо обычного ключевого слова `Sub`, потому что этот метод возвращает значение. Это объясняется просто: процедуры не возвращают значения, в отличие от функций.

1. Добавьте метод `CheckTheAnswer()`. Этот метод должен располагаться в строке с другими созданными методами, например `StartTheQuiz()`.

     При вызове этот метод складывает значения addend1 и addend2, а затем сравнивает результат со значением в элементе управления <xref:System.Windows.Forms.NumericUpDown> с именем sum. Если значения равны, метод возвращает значение `true`. В противном случае метод возвращает значение `false`. Код должен выглядеть так, как показано ниже.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Далее предстоит проверить ответ путем изменения кода в этом методе, чтобы обработчик события <xref:System.Windows.Forms.Timer.Tick> таймера вызвал новый метод `CheckTheAnswer()`.

2. Добавьте следующий код в инструкцию `if else` в методе `Timer1_Tick()`, чтобы таймер останавливался, когда пользователь получает право на ответ.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Если ответ правильный, `CheckTheAnswer()` возвращает значение `true`. Обработчик событий останавливает таймер, выводит поздравительное сообщение, а затем снова делает кнопку **Запуск** доступной. В противном случае головоломка продолжается.

3. Сохраните программу, запустите ее, запустите головоломку и введите правильный ответ на задачу сложения.

    > [!NOTE]
    > При вводе ответа необходимо либо выделить значение по умолчанию перед началом ввода ответа, либо удалить нуль вручную. Позднее в этом уроке мы исправим это поведение.

     При вводе правильного ответа появляется окно сообщения, кнопка **Запуск** становится доступной, и таймер останавливается.

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: **[Шаг 5. Добавление обработчиков событий входа для элементов управления NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)** .

- Предыдущий раздел руководства: [Шаг 3. Добавление таймера с обратным отсчетом](../ide/step-3-add-a-countdown-timer.md).
