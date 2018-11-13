---
title: Шаг 8. Настройка головоломки
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d020e2d83e7e631fefcb1503eb8f1938894986
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672123"
---
# <a name="step-8-customize-the-quiz"></a>Шаг 8. Настройка головоломки
В последней части этого руководства рассматривается несколько способов изменения викторины и приводятся дополнительные сведения по уже изученным вами вопросам. Например, можно подумать, как программа создает случайные задачи на деление, для которых ответ никогда не будет дробью. В качестве дополнительного занятия измените цвет элемента управления `timeLabel` и дайте игроку викторины подсказку.  

## <a name="to-customize-the-quiz"></a>Настройка викторины  

-   Когда для решения викторины останется лишь 5 секунд, измените цвет элемента управления **timeLabe** на красный путем задания свойства **BackColor** этого элемента управления (`timeLabel.BackColor = Color.Red;`). Восстановите цвет при завершении игры.  
  
-   Дайте игроку подсказку с помощью воспроизведения звука при вводе правильного ответа в элементе управления <xref:System.Windows.Forms.NumericUpDown>. (Необходимо написать обработчик событий для каждого события <xref:System.Windows.Forms.NumericUpDown.ValueChanged> элемента управления , который срабатывает при каждом изменении игроком значения элемента управления).  
  
## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Скачать готовую версию головоломки можно на странице с [полным примером руководства по созданию математической головоломки](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Следующее руководство: [Учебное руководство 3. Создание игры "Подбери пару!"](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Предыдущий раздел: [Шаг 7. Добавление задач на умножение и деление](../ide/step-7-add-multiplication-and-division-problems.md).
