---
title: Шаг 8. Настройка теста
description: Узнайте, как изменить цвет элемента управления timeLabel и дать игроку викторины подсказку.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 727d880caf912441009bda66bf516d501bd7303f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969650"
---
# <a name="step-8-customize-the-quiz"></a>Шаг 8. Настройка теста

В последней части этого руководства рассматривается несколько способов изменения викторины и приводятся дополнительные сведения по уже изученным вами вопросам. Например, можно подумать, как программа создает случайные задачи на деление, для которых ответ никогда не будет дробью. В качестве дополнительного занятия измените цвет элемента управления `timeLabel` и дайте игроку викторины подсказку.

> [!NOTE]
> Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-customize-the-quiz"></a>Настройка викторины

- Когда для решения головоломки останется лишь пять секунд, измените цвет элемента управления **timeLabel** на красный путем задания его свойства **BackColor**.

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Восстановите цвет при завершении игры.

- Дайте игроку подсказку с помощью воспроизведения звука при вводе правильного ответа в элементе управления <xref:System.Windows.Forms.NumericUpDown>. (Необходимо написать обработчик событий для каждого события <xref:System.Windows.Forms.NumericUpDown.ValueChanged> элемента управления , который срабатывает при каждом изменении игроком значения элемента управления).

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: **[Шаг 3. Создание игры "Подбери пару!"](../ide/tutorial-3-create-a-matching-game.md)** .

- Предыдущий раздел руководства: [Шаг 7. Добавление задач на умножение и деление](../ide/step-7-add-multiplication-and-division-problems.md).
