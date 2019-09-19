---
title: Шаг 8. Настройка теста
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86fb0b7d22e02e563fe022b470651e2c335e4000
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079459"
---
# <a name="step-8-customize-the-quiz"></a>Шаг 8. Настройка теста

В последней части этого руководства рассматривается несколько способов изменения викторины и приводятся дополнительные сведения по уже изученным вами вопросам. Например, можно подумать, как программа создает случайные задачи на деление, для которых ответ никогда не будет дробью. В качестве дополнительного занятия измените цвет элемента управления `timeLabel` и дайте игроку викторины подсказку.

> [!NOTE]
> Этот раздел входит в серию учебников, посвященных основам написания кода.
> - Общие сведения об учебнике см. в разделе [Руководство 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Скачать готовую версию кода можно на странице с [полным примером руководства по созданию математической головоломки](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-customize-the-quiz"></a>Настройка викторины

- Когда для решения головоломки останется лишь пять секунд, измените цвет элемента управления **timeLabel** на красный путем задания его свойства **BackColor**.

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  > [!IMPORTANT]
  > Используйте элемент управления языка программирования в правом верхнем углу этой страницы, чтобы просмотреть фрагмент кода на C# или Visual Basic.<br><br>![Элемент управления языка программирования для Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  Восстановите цвет при завершении игры.

- Дайте игроку подсказку с помощью воспроизведения звука при вводе правильного ответа в элементе управления <xref:System.Windows.Forms.NumericUpDown>. (Необходимо написать обработчик событий для каждого события <xref:System.Windows.Forms.NumericUpDown.ValueChanged> элемента управления , который срабатывает при каждом изменении игроком значения элемента управления).

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: **[Шаг 3. Создание игры "Подбери пару!"](../ide/tutorial-3-create-a-matching-game.md)** .

- Предыдущий раздел руководства: [Шаг 7. Добавление задач на умножение и деление](../ide/step-7-add-multiplication-and-division-problems.md).
