---
title: "Шаг 8. Настройка головоломки | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: "12"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 7a4481f9a13d6807abc42b938670a05bd0dda50b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="step-8-customize-the-quiz"></a>Шаг 8. Настройка головоломки
В последней части этого руководства рассматривается несколько способов изменения викторины и приводятся дополнительные сведения по уже изученным вами вопросам. Например, можно подумать, как программа создает случайные задачи на деление, для которых ответ никогда не будет дробью. В качестве дополнительного занятия измените цвет элемента управления `timeLabel` и дайте игроку викторины подсказку.  
  
### <a name="to-customize-the-quiz"></a>Настройка викторины  
  
-   Когда для решения викторины останется лишь 5 секунд, измените цвет элемента управления **timeLabe** на красный путем задания свойства **BackColor** этого элемента управления (`timeLabel.BackColor = Color.Red;`). Восстановите цвет при завершении игры.  
  
-   Дайте игроку подсказку с помощью воспроизведения звука при вводе правильного ответа в элементе управления NumericUpDown. (Необходимо написать обработчик событий для каждого события `ValueChanged()` элемента управления , который срабатывает при каждом изменении игроком значения элемента управления).  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Загрузить готовую версию головоломки можно на странице [Complete Math Quiz tutorial sample](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c) (Полный пример руководства по созданию математической головоломки).  
  
-   Следующее руководство см. на странице [(Учебное руководство 3. Создание игры "Подбери пару!")](../ide/tutorial-3-create-a-matching-game.md) (Учебное руководство 3. Создание игры "Подбери пару!").  
  
-   Предыдущий шаг руководства см. в разделе [Step 7: Add Multiplication and Division Problems](../ide/step-7-add-multiplication-and-division-problems.md) (Шаг 7. Добавление задач на умножение и деление).