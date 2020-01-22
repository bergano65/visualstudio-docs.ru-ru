---
title: Шаг 10. Написание кода для дополнительных кнопок и флажка
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 414e477dcc2e7b3bd4fcde6c82fe6c0ef77f1df0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113378"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Шаг 10. Написание кода для дополнительных кнопок и флажка

Теперь можно завершить другие четыре метода. Можно копировать и вставить этот код, но для получения дополнительных навыков введите код и используйте IntelliSense.

Этот код добавляет функциональность к ранее добавленным кнопкам. Без этого кода кнопки ничего не делают. Код используется в событиях <xref:System.Windows.Forms.Control.Click> кнопок (в случае флажка это событие <xref:System.Windows.Forms.CheckBox.CheckedChanged>) для выполнения различных действий при активации пользователем этих элементов управления. Например, событие `clearButton_Click` (или `ClearButton_Click`), которое активируется при нажатии кнопки **Очистить рисунок**, удаляет текущее изображение, присваивая его свойству **Image** значение **null** (или **nothing**). Каждое событие в коде сопровождается комментариями, которые поясняют, что делает код.

> [!TIP]
> Рекомендация: всегда снабжайте код комментариями. Комментарии — это сведения для человека, который читает код, необходимы для того, чтобы сделать код понятным. Содержимое в строке комментария игнорируется приложением. В C# строка комментария начинается с двух символов косой черты (//), а в Visual Basic — с одного знака одинарной кавычки (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Написание кода для дополнительных кнопок и флажка

Добавьте следующий код в файл кода **Form1** (*Form1.cs* или *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> В вашем коде буквы могут не отображаться в "верблюжьем" стиле.

## <a name="next-steps"></a>Следующие шаги

* Следующий раздел руководства: **[Шаг 11. Запуск приложения и изучение других функций](../ide/step-11-run-your-program-and-try-other-features.md)** .

* Предыдущий раздел руководства: [Шаг 9. Проверка, комментирование и тестирование кода](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>См. также

* [Учебник 2. Создание ограниченной по времени математической головоломки](tutorial-2-create-a-timed-math-quiz.md)
* [Учебник 3. Создание игры "Подбери пару!"](tutorial-3-create-a-matching-game.md)
