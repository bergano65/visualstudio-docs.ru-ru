---
title: Шаг 5. Добавление ссылок на метки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51512c80c96ef82835ce38c36e3643261ba84231
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671740"
---
# <a name="step-5-add-label-references"></a>Шаг 5. Добавление ссылок на метки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Программе необходимо отслеживать, какие элементы управления Label выбирает игрок. В настоящий момент программа отображает все метки, выбранные игроком. Однако мы изменим это. После выбора первой метки программа должна показывать ее значок. После выбора второй метки программа должна показать оба значка на короткое время, а затем снова скрыть их. Теперь программа будет отследить, какой элемент управления Label выбирается первым, а какие — в секунду, используя *Ссылочные переменные*.

### <a name="to-add-label-references"></a>Добавление ссылок на метки

1. Добавьте ссылки на метки в свою форму, используя следующий код.

     [!code-csharp[VbExpressTutorial4Step5#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial4Step5#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#5)]

     Ссылочные переменные похожи на операторы, которые вы использовали для добавления объектов (таких как объекты `Timer`, `List` и `Random`) в форму. Однако эти операторы не приводят к появлению в форме двух дополнительных меток, поскольку в них не используется ключевое слово `new`. Без ключевого слова `new` объект не создается. Именно поэтому `firstClicked` и `secondClicked` называются ссылочными переменными — они просто отслеживают (или ссылаются на) объекты `Label`.

     Когда переменная не отслеживает объект, ей задается специальное зарезервированное значение — `null` в Visual C# и `Nothing` в Visual Basic. Поэтому при запуске программы переменным `firstClicked`и `secondClicked` задается значение `null` или `Nothing`. Это означает, что переменные ничего не отслеживают.

2. Измените свой обработчик событий Click для использования новой ссылочной переменной `firstClicked`. Удалите последний оператор (`label_Click()`) в методе обработчика событий `clickedLabel.ForeColor = Color.Black;` и замените его последующим оператором `if`. (Не забудьте включить комментарий и весь оператор `if`).

     [!code-csharp[VbExpressTutorial4Step5#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial4Step5#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#6)]

3. Сохраните и выполните программу. Выберите одну из меток и появится ее значок.

4. Выберите следующую метку и обратите внимание, что ничего не происходит. Программа уже отслеживает первую метку, которую выбрал игрок, поэтому `firstClicked` не равно `null` в Visual C# или `Nothing` в Visual Basic. Когда оператор `if` проверяет, имеет ли переменная `firstClicked` значение `null` или `Nothing`, он обнаруживает, что это не так, и не выполняет операторы в блоке `if`. Поэтому только первый выбранный значок становится черным, а другие значки остаются невидимыми, как показано на следующем рисунке.

     ![Игра, отображающая один значок](../ide/media/express-tut4step5.png "Express_Tut4Step5") Игра, отображающая один значок

     Это поведение будет исправлено в следующем шаге руководства путем добавления элемента управления **Таймер**.

### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий шаг руководства см. в разделе [Шаг 6. Добавление таймера](../ide/step-6-add-a-timer.md).

- Предыдущий шаг руководства см. в разделе [Шаг 4. Добавление обработчика событий щелчка к каждой метке](../ide/step-4-add-a-click-event-handler-to-each-label.md).
