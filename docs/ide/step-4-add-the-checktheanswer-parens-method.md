---
title: "Шаг 4. Добавление метода CheckTheAnswer() | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: "19"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 49ef6cd4456f920fed0eb612da0e0a81368f6be5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="step-4-add-the-checktheanswer-method"></a>Шаг 4. Добавление метода CheckTheAnswer()
В четвертой части этого урока вам предстоит написать метод `CheckTheAnswer()`, который проверяет правильность ответов на арифметические задачи. Этот раздел входит в серию учебников, посвященных основам написания кода. Обзор учебника см. в статье [Tutorial 2: Create a Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md) (Учебное руководство 2. Создание ограниченной по времени математической головоломки).  
  
> [!NOTE]
>  Если вы разрабатываете головоломку на Visual Basic, вам необходимо будет использовать ключевое слово `Function` вместо обычного ключевого слова `Sub`, потому что этот метод возвращает значение. Это объясняется просто: процедуры не возвращают значения, в отличие от функций.  
  
### <a name="to-verify-whether-the-answers-are-correct"></a>Проверка правильности ответов  
  
1.  Добавьте метод `CheckTheAnswer()`.  
  
     При вызове этот метод складывает значения addend1 и addend2, а затем сравнивает результат со значением в элементе управления `NumericUpDown` с именем sum. Если значения равны, метод возвращает значение `true`. В противном случае метод возвращает значение `false`. Код должен выглядеть так, как показано ниже.  
  
     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]  
  
     Далее предстоит проверить ответ путем изменения кода в этом методе, чтобы обработчик события Tick таймера вызвал новый метод `CheckTheAnswer()`.  
  
2.  Добавьте следующий код в оператор `if else`.  
  
     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]  
  
     Если ответ правильный, `CheckTheAnswer()` возвращает значение `true`. Обработчик событий останавливает таймер, выводит поздравительное сообщение, а затем снова делает кнопку **Запуск** доступной. В противном случае головоломка продолжается.  
  
3.  Сохраните программу, запустите ее, запустите головоломку и введите правильный ответ на задачу сложения.  
  
    > [!NOTE]
    >  При вводе ответа необходимо либо выделить значение по умолчанию перед началом ввода ответа, либо удалить нуль вручную. Позднее в этом уроке мы исправим это поведение.  
  
     При вводе правильного ответа появляется окно сообщения, кнопка **Запуск** становится доступной, и таймер останавливается.  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Следующий шаг руководства см. в разделе [Step 5: Add Enter Event Handlers for the NumericUpDown Controls](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md) (Шаг 5. Добавление обработчиков событий входа для элементов управления NumericUpDown).  
  
-   Предыдущий шаг руководства см. в разделе [Step 3: Add a Countdown Timer](../ide/step-3-add-a-countdown-timer.md) (Шаг 6. Добавление таймера с обратным отсчетом).