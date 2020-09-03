---
title: Шаг 6. Добавление задачи на вычитание | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ec0bdd3ebae52158c5631a880e63ee0f3a455de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671714"
---
# <a name="step-6-add-a-subtraction-problem"></a>Шаг 6. Добавление задачи на вычитание
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В шестой части этого учебника вам предстоит добавить задачу на вычитание и научиться выполнять следующие задачи:

- Хранение значений, которые участвуют в операции вычитания.

- Создание случайных чисел для задачи (а также гарантия, что ответ лежит в диапазоне от 0 до 100).

- Обновление метода, который проверяет ответы, таким образом, чтобы он также проверял новую задачу на вычитание.

- Обновление обработчика событий таймера Tick таким образом, чтобы этот обработчик событий заполнял корректный ответ после истечения времени.

### <a name="to-add-a-subtraction-problem"></a>Добавление задачи на вычитание

1. Добавьте в форму две целочисленные переменные для задачи на вычитание — между целочисленными переменными для задачи на сложение и для таймера. Код должен выглядеть следующим образом.

     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]

     Имена новых целочисленных переменных — **minuend** и **subtrahend** — не являются терминами программирования. Это принятые в арифметике обозначения для числа, которое вычитается из другого числа (subtrahend — вычитаемое), и числа, из которого производится вычитание (minuend — уменьшаемое). Остаток — это уменьшаемое за минусом вычитаемого. Можно использовать другие имена, так как программа не требует определенных имен для переменных, элементов управления, компонентов или методов. Необходимо соблюдать правила — например, не начинать имена с цифр — но вообще можно использовать такие имена, как x1, x2, x3 и x4. Однако универсальные имена ухудшают читабельность кода, и при возникновении проблем отследить их источник становится практически невозможно. Чтобы имена переменных были уникальными и информативными, для умножения и деления далее в этом учебнике мы также будем использовать традиционные имена: multiplicand (множимое) × multiplier (множитель) = product (произведение); dividend (делимое) ÷ divisor (делитель) = quotient (частное).

     Затем необходимо изменить метод `StartTheQuiz()`, чтобы получить случайные значения для задачи на вычитание.

2. Добавьте после комментария "Fill in the subtraction problem" (Заполнение задачи на вычитание) следующий код.

     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]

     Чтобы в задаче на вычитание не было отрицательных ответов, метод `Next()` класса `Random` в этом коде используется несколько иначе, чем в задаче на сложение. Когда методу `Next()` передается два значения, он выбирает случайное число, которое больше первого значения или равно ему и меньше второго значения. Следующий код выбирает случайное число в диапазоне от 1 до 100 и сохраняет его в переменной minuend.

     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]

     Вызвать метод `Next()` класса `Random`, который мы ранее в этом руководстве назвали "randomizer", можно различными способами. Методы, которые можно вызывать несколькими способами, называются перегруженными. Для их изучения можно использовать IntelliSense. Посмотрите еще раз на всплывающую подсказку окна IntelliSense для метода `Next()`.

     ![Подсказка окна IntelliSense](../ide/media/express-overloads.png "Express_Overloads") Подсказка окна IntelliSense

     В подсказке сказано **(+2 перегрузки)**, что означает, что вызвать метод `Next()` можно еще двумя способами. Перегрузки методов содержат разное количество или типы аргументов, поэтому работают слегка по-разному. Например, метод может принимать один целочисленный аргумент, тогда как одна из его перегрузок может принимать целое число и строку. Выбирайте подходящую перегрузку в зависимости от того, что требуется сделать. При добавлении кода в метод `StartTheQuiz()` в окне Intellisense появляется дополнительная информация, как только вы введете `randomizer.Next(`. Нажимайте клавиши СТРЕЛКА ВВЕРХ и СТРЕЛКА ВНИЗ для перебора перегрузок, как показано на следующем рисунке.

     ![Перегрузка метода Next() в IntelliSense](../ide/media/express-nextoverload.png "Express_NextOverload") Перегрузка метода Next() в IntelliSense

     В данном случае необходимо выбрать последнюю перегрузку, чтобы можно было задать минимальное и максимальное значения.

3. Для проверки правильного ответа для задачи на вычитание, измените метод `CheckTheAnswer()`.

     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]

     В Visual C# `&&` — это оператор `logical and` . Эквивалентный оператор в языке Visual Basic — `AndAlso`. Эти операторы означают, что "Если addend1 плюс addend2 равно значению NumericUpDown с именем sum и если minuend минус subtrahend равно значению NumericUpDown с именем difference". Метод `CheckTheAnswer()` возвращает значение `true`, только если игрок дал правильные ответы и на задачу на сложение, и на задачу на вычитание.

4. Замените последнюю часть обработчика событий таймера Tick следующим кодом, чтобы по истечении времени этот обработчик событий проставлял правильный ответ.

     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]

5. Сохраните и выполните код.

     Теперь программа включает в себя задачу на вычитание, как показано на следующем рисунке.

     ![Математическая головоломка с проблемой вычитания](../ide/media/express-addsubtract.png "Express_AddSubtract") Математическая головоломка с проблемой вычитания

### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий шаг руководства см. в разделе [Шаг 7. Добавление проблем с умножением и делением](../ide/step-7-add-multiplication-and-division-problems.md).

- Предыдущий шаг руководства см. в разделе [Шаг 5. Добавление обработчиков событий ввода для элементов управления NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
