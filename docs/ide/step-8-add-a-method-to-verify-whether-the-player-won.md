---
title: "Шаг 8. Добавление метода для проверки того, выиграл ли игрок | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: "17"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e57a4e8d7d4a46b9938c5d2fe5a2bb6612309dc9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Шаг 8. Добавление метода для проверки, выиграл ли игрок
Вы создали интересную игру, но требуется еще один элемент, чтобы завершить ее. Игра должна заканчиваться победой игрока, поэтому необходимо добавить метод `CheckForWinner()` для проверки, выиграл ли игрок.  
  
### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Добавление метода для проверки, выиграл ли игрок  
  
1.  Добавьте метод `CheckForWinner()` в нижнюю часть кода, под обработчиком событий `timer1_Tick()`, как показано в следующем коде.  
  
     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]  
  
     В этом методе используется еще один цикл `foreach` для C# или цикл `For Each` для Visual Basic, чтобы пройти по каждой метке в TableLayoutPanel. Он использует оператор равенства (`==` в Visual C# и `=` в Visual Basic) для проверки цвета значка каждой метки на соответствие цвету фона. Если цвета совпадают, значок остается невидимым, а значит игрок не подобрал пару оставшимся значкам. В этом случае программа использует оператор `return`, чтобы пропустить оставшуюся часть метода. Если цикл прошел через все метки без выполнения оператора `return`, значит, всем значкам в форме была подобрана пара. Программа отображает окно MessageBox с поздравлением победителя, а затем вызывает метод формы `Close()` для завершения игры.  
  
2.  После этого обработчик событий Click метки вызывает новый метод `CheckForWinner()`. Убедитесь, что программа проверяет наличие победителя сразу после отображения второго значка, который выбирает игрок. Найдите строку, где задается цвет второму значку, который вы выбрали, и после этой операции вызовите метод `CheckForWinner()`, как показано в следующем коде.  
  
     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]  
  
3.  Сохраните и выполните программу. Сыграйте в игру и подберите пару всем значкам. Если вы победили, программа отображает сообщение MessageBox с поздравлением (как показано на следующем рисунке) и закрывает окно.  
  
     ![Игра "Подбери пару!" с MessageBox](../ide/media/express_tut4step8.png "Express_Tut4Step8")  
Игра "Подбери пару!" с MessageBox  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Следующий шаг руководства см. в разделе [Шаг 9. Изучение других возможностей](../ide/step-9-try-other-features.md).  
  
-   Предыдущий шаг руководства см. в разделе [Шаг 7. Отмена исчезновения пар значков](../ide/step-7-keep-pairs-visible.md).