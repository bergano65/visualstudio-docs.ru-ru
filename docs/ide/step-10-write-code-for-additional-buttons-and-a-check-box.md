---
title: Шаг 10. Написание кода для дополнительных кнопок и флажка
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9763026a4ef1c219bcb9f5b5270ac5d3b48e2e14
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887866"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Шаг 10. Написание кода для дополнительных кнопок и флажка

Теперь можно завершить другие четыре метода. Можно копировать и вставить этот код, но для получения дополнительных навыков введите код и используйте IntelliSense.

Этот код добавляет функциональность к ранее добавленным кнопкам. Без этого кода кнопки ничего не делают. Код используется в событиях <xref:System.Windows.Forms.Control.Click> кнопок (в случае флажка это событие <xref:System.Windows.Forms.CheckBox.CheckedChanged>) для выполнения различных действий при активации пользователем этих элементов управления. Например, событие `clearButton_Click` (или `ClearButton_Click`), которое активируется при нажатии кнопки **Очистить рисунок**, удаляет текущее изображение, присваивая его свойству **Image** значение **null** (или **nothing**). Каждое событие в коде сопровождается комментариями, которые поясняют, что делает код.

> [!TIP]
> Рекомендация: всегда снабжайте код комментариями. Комментарии — это сведения для человека, который читает код, необходимы для того, чтобы сделать код понятным. Содержимое в строке комментария игнорируется приложением. В C# строка комментария начинается с двух символов косой черты (//), а в Visual Basic — с одного знака одинарной кавычки (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Написание кода для дополнительных кнопок и флажка

Добавьте следующий код в файл кода **Form1** (*Form1.cs* или *Form1.vb*).
> [!IMPORTANT]
> Используйте элемент управления языка программирования в правом верхнем углу этой страницы, чтобы просмотреть фрагмент кода на C# или Visual Basic.<br><br>![Элемент управления языка программирования для Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

## <a name="next-steps"></a>Следующие шаги

* Следующий раздел руководства: **[Шаг 11. Запуск приложения и изучение других функций](../ide/step-11-run-your-program-and-try-other-features.md)** .

* Предыдущий раздел руководства: [Шаг 9. Проверка, комментирование и тестирование кода](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>См. также

* [Учебник 2. Создание ограниченной по времени математической головоломки](tutorial-2-create-a-timed-math-quiz.md)
* [Учебник 3. Создание игры "Подбери пару!"](tutorial-3-create-a-matching-game.md)
