---
title: Шаг 4. Добавление метода CheckTheAnswer() | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9806bad150a5d03a942c7dfb36753f91d10536e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442565"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Шаг 4. Добавление метода CheckTheAnswer()
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В четвертой части этого урока вам предстоит написать метод `CheckTheAnswer()`, который проверяет правильность ответов на арифметические задачи. Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание математической викторины](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
> Если вы разрабатываете головоломку на Visual Basic, вам необходимо будет использовать ключевое слово `Function` вместо обычного ключевого слова `Sub`, потому что этот метод возвращает значение. Это объясняется просто: процедуры не возвращают значения, в отличие от функций.  
  
### <a name="to-verify-whether-the-answers-are-correct"></a>Проверка правильности ответов  
  
1. Добавьте метод `CheckTheAnswer()`.  
  
     При вызове этот метод складывает значения addend1 и addend2, а затем сравнивает результат со значением в элементе управления `NumericUpDown` с именем sum. Если значения равны, метод возвращает значение `true`. В противном случае метод возвращает значение `false`. Код должен выглядеть так, как показано ниже.  
  
     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]  
  
     Далее предстоит проверить ответ путем изменения кода в этом методе, чтобы обработчик события Tick таймера вызвал новый метод `CheckTheAnswer()`.  
  
2. Добавьте следующий код в оператор `if else`.  
  
     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]  
  
     Если ответ правильный, `CheckTheAnswer()` возвращает значение `true`. Обработчик событий останавливает таймер, выводит поздравительное сообщение, а затем снова делает кнопку **Запуск** доступной. В противном случае головоломка продолжается.  
  
3. Сохраните программу, запустите ее, запустите головоломку и введите правильный ответ на задачу сложения.  
  
    > [!NOTE]
    > При вводе ответа необходимо либо выделить значение по умолчанию перед началом ввода ответа, либо удалить нуль вручную. Позднее в этом уроке мы исправим это поведение.  
  
     При вводе правильного ответа появляется окно сообщения, кнопка **Запуск** становится доступной, и таймер останавливается.  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
- Следующий раздел руководства: [Шаг 5. Добавление обработчиков событий входа для элементов управления NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
- Предыдущий раздел руководства: [Шаг 3. Добавление таймера с обратным отсчетом](../ide/step-3-add-a-countdown-timer.md).
