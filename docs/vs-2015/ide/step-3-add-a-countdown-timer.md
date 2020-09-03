---
title: Шаг 3. Добавление таймера с обратным отсчетом | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bae5b4a81864cc591491c21218a5d8253dfc61bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671847"
---
# <a name="step-3-add-a-countdown-timer"></a>Шаг 3. Добавление таймера с обратным отсчетом
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В третьей части этого учебника вам предстоит добавить таймер обратного отсчета для отслеживания количества секунд, оставшихся у игрока на решение задач викторины.

> [!NOTE]
> Этот раздел входит в серию учебников, посвященных основам написания кода. Обзор этого руководства см. в разделе [учебник 2. Создание математической головоломки с течением времени](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-add-a-countdown-timer"></a>Добавление таймера с обратным отсчетом

1. Добавьте целочисленную переменную с именем **timeLeft** точно так же, как в предыдущей процедуре. Код должен выглядеть так, как показано ниже.

     [!code-csharp[VbExpressTutorial3Step3#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial3Step3#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#5)]

     Теперь вам необходим метод-таймер, который будет подсчитывать количество секунд и по истечении указанного времени вызывать событие.

2. В окне конструктора переместите элемент управления `Timer` из категории **Компоненты** на панели элементов на свою форму.

     Элемент управления появляется в серой области в нижней части окна конструктора.

3. Щелкните в форме только что добавленный значок **timer1** и установите его свойство **Interval** равным **1000**.

     Поскольку значение интервала указывается в миллисекундах, при значении 1000 событие Tick будет запускаться каждую секунду.

4. Двойным щелчком выберите в форме элемент управления Timer либо выделите его и нажмите клавишу ВВОД.

     Появится редактор кода с отображением метода для только что добавленного обработчика событий Tick.

5. Добавьте в новый метод обработчика событий следующие операторы.

     [!code-csharp[VbExpressTutorial3Step3#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial3Step3#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#6)]

     Основываясь на добавленных операторах, таймер каждую секунду проверяет, истекло ли время, путем проверки того, является ли целочисленная переменная **timeLeft** больше 0. Если она больше 0, время еще осталось. Таймер сначала вычитает 1 из значения переменной timeLeft, а затем обновляет свойство **Text** элемента управления `timeLabel`, чтобы показать игроку, сколько осталось секунд.

     Если времени не осталось, таймер останавливается и изменяет текст в элементе управления `timeLabel` так, чтобы он показывал **Time's up!** (Время вышло!). Появляется окно сообщения о том, что игра закончена, и отображается ответ — в данном случае сумма переменной addend1 и переменной addend2. Свойству **Enabled** элемента управления `startButton` устанавливается значение `true`, чтобы игрок мог заново запустить викторину.

     Только что был добавлен оператор `if else`, в котором описывается, как программа принимает решение . Оператор `if else` представлен ниже.

    > [!NOTE]
    > Следующий пример приведен исключительно для иллюстрации; не добавляйте его в свой проект.

    ```vb
    If (something that your program will check) Then
        ' One or more statements that will run
        ' if what the program checked is true.
    Else
        ' One or more statements that will run
        ' if what the program checked is false.
    End If
    ```

    ```csharp
    if (something that your program will check)
    {
        // One or more statements that will run
        // if what the program checked is true.
    }
    else
    {
        // One or more statements that will run
        // if what the program checked is false.
    }
    ```

     Внимательно рассмотрите оператор, который вы добавили в блок `else`, чтобы отобразить ответ на задачу на сложение.

     [!code-csharp[VbExpressTutorial3Step3#24](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#24)]
     [!code-vb[VbExpressTutorial3Step3#24](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#24)]

     Оператор `addend1 + addend2` складывает значения двух переменных. Первая часть (`sum.Value`) использует свойство **Value** элемента управления `NumericUpDown` суммы для отображения правильного ответа. Это же свойство позднее используется для проверки ответов на головоломку.

     Элемент управления `NumericUpDown` позволяет игрокам легко вводить числа; именно поэтому мы используем его для ответов на арифметические задачи. Все возможные ответы представляют собой целые числа в диапазоне от 0 до 100. Оставив для свойств **Minimum**, **Maximum** и **DecimalPlaces** значения по умолчанию, вы гарантируете, что игроки не смогут вводить десятичные знаки, отрицательные числа или слишком большие числа. (Если, например, требуется разрешить игрокам ввести 3,141, но не 3,1415, можно задать для свойства **DecimalPlaces** значение, равное 3.)

6. Добавьте три строки в конец метода `StartTheQuiz()`, чтобы код выглядел так, как показано ниже.

     [!code-csharp[VbExpressTutorial3Step3#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial3Step3#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#7)]

     Теперь при запуске головоломки переменная **timeLeft** устанавливается равной 30, а свойство **Text** элемента управления `timeLabel` устанавливается равным 30 секундам. После этого метод `Start()` элемента управления `Timer` начинает обратный отсчет. (Ответ пока не проверяется — это делается позже.)

7. Сохраните программу, запустите ее и нажмите кнопку **Запуск** в форме.

     Таймер начинает обратный отсчет. Когда время истечет, игра закончится и появится ответ. На следующем рисунка показана головоломка в процессе игры.

     ![Math quiz in progress](../ide/media/express-addcountdown.png "Express_AddCountdown") Математическая головоломка в процессе игры

### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Чтобы перейти к следующему шагу руководства, см. [Шаг 4. Добавление метода метода CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md).

- Чтобы вернуться к предыдущему шагу руководства, см. [Шаг 2. Создание задачи на сложение случайных чисел](../ide/step-2-create-a-random-addition-problem.md).
