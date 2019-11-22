---
title: Учебное руководство 3. Создание игры "Подбери пару!" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 30ee029fe231202c821c8448d3594192b5ebfdf8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299848"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutorial 3: Create a Matching Game
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом учебном руководстве вы создадите игру "Подбери пару!", в которой игрок должен подобрать пару скрытым значкам. Вы научитесь:

- сохранять объекты, например значки, в объекте `List`;

- использовать цикл `foreach` в Visual C# или цикл `For Each` в Visual Basic для перебора элементов в списке;

- отслеживать состояние формы с помощью ссылочных переменных;

- создавать обработчик событий, который можно использовать для нескольких объектов;

- создавать таймер, который отсчитывает время и вызывает событие ровно один раз после запуска.

  После прохождения этого учебного руководства ваша программа будет выглядеть так, как показано на следующем рисунке.

  ![Game that you create in this tutorial](../ide/media/express-finishedgame.png "Express_FinishedGame") Игра, созданная в этом учебнике

> [!NOTE]
> В этом учебном руководстве показаны примеры, как на Visual C#, так и на Visual Basic, поэтому обратите внимание на информацию, которая относится к используемому вами языку программирования.

 Если у вас возникли затруднения или вопросы по программированию, попробуйте задать вопрос на одном из форумов MSDN. См. [Форум Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) и [Форум Visual C#](https://social.msdn.microsoft.com/Forums/en-US/home). Кроме того, вы можете найти отличные бесплатные учебные видеоматериалы. Дополнительные сведения о программировании на языке Visual Basic см. в разделе [Основы Visual Basic: разработка для начинающих](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Дополнительные сведения о программировании на языке Visual C# см. в разделе [Основы Visual C#: разработка для начинающих](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Шаг 1. Создание проекта и добавление таблицы в форму](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Начните с создания проекта и добавления элемента управления `TableLayoutPanel`, чтобы все элементы управления были правильно выровнены.|
|[Шаг 2. Добавление случайного объекта и списка значков](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Добавление объектов `Random` и `List` для создания списка значков.|
|[Шаг 3. Назначение каждой метке случайного значка](../ide/step-3-assign-a-random-icon-to-each-label.md)|Случайным образом назначьте значки элементам управления `Label`, чтобы каждая игра отличалась от остальных.|
|[Шаг 4. Добавление к каждой метке обработчика событий щелчка мышью](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Добавление обработчика события Click, изменяющего цвет метки, которую щелкнули.|
|[Шаг 5. Добавление ссылок на метки](../ide/step-5-add-label-references.md)|Добавление ссылочных переменных для отслеживания меток, которые щелкнули.|
|[Шаг 6. Добавление таймера](../ide/step-6-add-a-timer.md)|Добавьте таймер в форму, чтобы отслеживать время, прошедшее с начала игры.|
|[Шаг 7. Отмена исчезновения пар значков](../ide/step-7-keep-pairs-visible.md)|Отмена исчезновения пар значков, если выбрана одинаковая пара.|
|[Шаг 8. Добавление метода для проверки, выиграл ли игрок](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Добавление метода `CheckForWinner()` для проверки, выиграл ли игрок.|
|[Шаг 9. Изучение других возможностей](../ide/step-9-try-other-features.md)|Изучение других функций, таких как изменение значков и цветов, добавление сетки и добавление звуков. Увеличение игрового поля и изменение настроек таймера.|
