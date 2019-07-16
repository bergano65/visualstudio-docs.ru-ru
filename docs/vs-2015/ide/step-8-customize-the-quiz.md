---
title: Шаг 8. Настройка головоломки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 75bde59c6e4b61c2775f188383fc9058a6c31242
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178549"
---
# <a name="step-8-customize-the-quiz"></a>Шаг 8. Настройка теста
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В последней части этого руководства рассматривается несколько способов изменения викторины и приводятся дополнительные сведения по уже изученным вами вопросам. Например, можно подумать, как программа создает случайные задачи на деление, для которых ответ никогда не будет дробью. В качестве дополнительного занятия измените цвет элемента управления `timeLabel` и дайте игроку викторины подсказку.  
  
### <a name="to-customize-the-quiz"></a>Настройка викторины  
  
- Когда для решения викторины останется лишь 5 секунд, измените цвет элемента управления **timeLabe** на красный путем задания свойства **BackColor** этого элемента управления (`timeLabel.BackColor = Color.Red;`). Восстановите цвет при завершении игры.  
  
- Дайте игроку подсказку с помощью воспроизведения звука при вводе правильного ответа в элементе управления NumericUpDown. (Необходимо написать обработчик событий для каждого события `ValueChanged()` элемента управления , который срабатывает при каждом изменении игроком значения элемента управления).  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
- Загрузить готовую версию головоломки можно на странице [Complete Math Quiz tutorial sample](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c) (Полный пример руководства по созданию математической головоломки).  
  
- Следующее руководство см. в разделе [ Руководство 3. Создать соответствующий игру](../ide/tutorial-3-create-a-matching-game.md).  
  
- Предыдущий раздел руководства: [Шаг 7. Добавление задач на умножение и деление](../ide/step-7-add-multiplication-and-division-problems.md).
