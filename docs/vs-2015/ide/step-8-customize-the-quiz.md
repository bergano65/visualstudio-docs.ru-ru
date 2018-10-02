---
title: Шаг 8. Настройка головоломки | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72e630a3d065e196d33919045316fad27c912750
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571929"
---
# <a name="step-8-customize-the-quiz"></a>Шаг 8. Настройка головоломки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [шаг 8: Настройка головоломки](https://docs.microsoft.com/visualstudio/ide/step-8-customize-the-quiz).  
  
В последней части этого руководства рассматривается несколько способов изменения викторины и приводятся дополнительные сведения по уже изученным вами вопросам. Например, можно подумать, как программа создает случайные задачи на деление, для которых ответ никогда не будет дробью. В качестве дополнительного занятия измените цвет элемента управления `timeLabel` и дайте игроку викторины подсказку.  
  
### <a name="to-customize-the-quiz"></a>Настройка викторины  
  
-   Когда для решения викторины останется лишь 5 секунд, измените цвет элемента управления **timeLabe** на красный путем задания свойства **BackColor** этого элемента управления (`timeLabel.BackColor = Color.Red;`). Восстановите цвет при завершении игры.  
  
-   Дайте игроку подсказку с помощью воспроизведения звука при вводе правильного ответа в элементе управления NumericUpDown. (Необходимо написать обработчик событий для каждого события `ValueChanged()` элемента управления , который срабатывает при каждом изменении игроком значения элемента управления).  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Загрузить готовую версию головоломки можно на странице [Complete Math Quiz tutorial sample](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c) (Полный пример руководства по созданию математической головоломки).  
  
-   Следующее руководство см. на странице [(Учебное руководство 3. Создание игры "Подбери пару!")](../ide/tutorial-3-create-a-matching-game.md) (Учебное руководство 3. Создание игры "Подбери пару!").  
  
-   Предыдущий шаг руководства см. в разделе [Step 7: Add Multiplication and Division Problems](../ide/step-7-add-multiplication-and-division-problems.md) (Шаг 7. Добавление задач на умножение и деление).



