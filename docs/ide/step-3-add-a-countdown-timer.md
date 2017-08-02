---
title: "Шаг 3. Добавление таймера с обратным отсчетом | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 23
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 451635681519303b5e85b70788534e22af21707c
ms.contentlocale: ru-ru
ms.lasthandoff: 05/13/2017

---
# <a name="step-3-add-a-countdown-timer"></a>Шаг 3. Добавление таймера с обратным отсчетом
В третьей части этого учебника вам предстоит добавить таймер обратного отсчета для отслеживания количества секунд, оставшихся у игрока на решение задач викторины.  
  
> [!NOTE]
>  Этот раздел входит в серию учебников, посвященных основам написания кода. Обзор учебника см. в статье [Tutorial 2: Create a Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md) (Учебное руководство 2. Создание ограниченной по времени математической головоломки).  
  
### <a name="to-add-a-countdown-timer"></a>Добавление таймера с обратным отсчетом  
  
1.  Добавьте целочисленную переменную с именем **timeLeft** точно так же, как в предыдущей процедуре. Код должен выглядеть так, как показано ниже.  
  
     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)] [!code-cs[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]  
  
     Теперь вам необходим метод-таймер, который будет подсчитывать количество секунд и по истечении указанного времени вызывать событие.  
  
2.  В окне конструктора переместите элемент управления `Timer` из категории **Компоненты** панели элементов на свою форму.  
  
     Элемент управления появляется в серой области в нижней части окна конструктора.  
  
3.  Щелкните в форме только что добавленный значок **timer1** и установите его свойство **Interval** равным **1000**.  
  
     Поскольку значение интервала указывается в миллисекундах, при значении 1000 событие Tick будет запускаться каждую секунду.  
  
4.  Двойным щелчком выберите в форме элемент управления Timer либо выделите его и нажмите клавишу ВВОД.  
  
     Появится редактор кода с отображением метода для только что добавленного обработчика событий Tick.  
  
5.  Добавьте в новый метод обработчика событий следующие операторы.  
  
     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)] [!code-cs[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]  
  
     Основываясь на добавленных операторах, таймер каждую секунду проверяет, истекло ли время, путем проверки того, является ли целочисленная переменная **timeLeft** больше 0. Если она больше 0, время еще осталось. Таймер сначала вычитает 1 из значения переменной timeLeft, а затем обновляет свойство **Text** элемента управления `timeLabel`, чтобы показать игроку, сколько осталось секунд.  
  
     Если времени не осталось, таймер останавливается и изменяет текст в элементе управления `timeLabel` так, чтобы он показывал **Time's up!** (Время вышло!). Появляется окно сообщения о том, что игра закончена, и отображается ответ — в данном случае сумма переменной addend1 и переменной addend2. Свойству **Enabled** элемента управления `startButton` устанавливается значение `true`, чтобы игрок мог заново запустить викторину.  
  
     Только что был добавлен оператор `if else`, в котором описывается, как программа принимает решение . Оператор `if else` представлен ниже.  
  
    > [!NOTE]
    >  Следующий пример приведен исключительно для иллюстрации; не добавляйте его в свой проект.  
  
    ```vb  
    If (something that your program will check) Then  
        ' One or more statements that will run  
        ' if what the program checked is true.   
    Else  
        ' One or more statements that will run  
        ' if what the program checked is false.  
    End If  
    ```  
  
    ```c#  
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
  
     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)] [!code-cs[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]  
  
     Оператор `addend1 + addend2` складывает значения двух переменных. Первая часть (`sum.Value`) использует свойство **Value** элемента управления `NumericUpDown` суммы для отображения правильного ответа. Это же свойство позднее используется для проверки ответов на головоломку.  
  
     Элемент управления `NumericUpDown` позволяет игрокам легко вводить числа; именно поэтому мы используем его для ответов на арифметические задачи. Все возможные ответы представляют собой целые числа в диапазоне от 0 до 100. Оставив для свойств **Minimum**, **Maximum** и **DecimalPlaces** значения по умолчанию, вы гарантируете, что игроки не смогут вводить десятичные знаки, отрицательные числа или слишком большие числа. (Если, например, требуется разрешить игрокам ввести 3,141, но не 3,1415, можно задать для свойства **DecimalPlaces** значение, равное 3.)  
  
6.  Добавьте три строки в конец метода `StartTheQuiz()`, чтобы код выглядел так, как показано ниже.  
  
     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)] [!code-cs[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]  
  
     Теперь при запуске головоломки переменная **timeLeft** устанавливается равной 30, а свойство **Text** элемента управления `timeLabel` устанавливается равным 30 секундам. После этого метод `Start()` элемента управления `Timer` начинает обратный отсчет. (Ответ пока не проверяется — это делается позже.)  
  
7.  Сохраните программу, запустите ее и нажмите кнопку **Запуск** в форме.  
  
     Таймер начинает обратный отсчет. Когда время истечет, игра закончится и появится ответ. На следующем рисунка показана головоломка в процессе игры.  
  
     ![Математическая головоломка в процессе игры](~/docs/ide/media/express_addcountdown.png "Express_AddCountdown")  
Математическая головоломка в процессе игры  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Следующий шаг руководства см. в разделе [Step 4: Add the CheckTheAnswer() Method](../ide/step-4-add-the-checktheanswer-parens-method.md) (Шаг 4. Добавление метода CheckTheAnswer()).  
  
-   Предыдущий шаг руководства см. в разделе [Step 2: Create a Random Addition Problem](../ide/step-2-create-a-random-addition-problem.md) (Шаг 6. Создание задачи на сложение случайных чисел).
