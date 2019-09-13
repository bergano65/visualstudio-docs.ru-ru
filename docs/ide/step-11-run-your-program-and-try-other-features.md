---
title: Шаг 11. Запуск приложения и изучение других функций
ms.date: 08/30/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e82e0002255a406f02f85cbb2636be1aa249529
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887949"
---
# <a name="step-11-run-your-app-and-try-other-features"></a>Шаг 11. Запуск приложения и изучение других функций

Разработка приложения завершена, и оно готово для выполнения. Вы можете запустить приложение и задать цвет фона для <xref:System.Windows.Forms.PictureBox>. В качестве дополнительного занятия попробуйте улучшить приложение, изменив цвет формы, настроив кнопки и флажки и изменив свойства формы.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Запуск приложения и настройка цвета фона

1. Нажмите клавишу **F5** или в строке меню выберите **Отладка** > **Начать отладку**.

1. Прежде чем открыть изображение, нажмите кнопку **Установить цвет фона**. Откроется диалоговое окно **Цвет**.

     ![Диалоговое окно "Цвет"](../ide/media/express_colordialog.png)<br/>
*Диалоговое окно* ***Цвет***

1. Выберите цвет фона для элемента управления PictureBox. Внимательно просмотрите метод `backgroundButton_Click()` (или `BackgroundButton_Click()`), чтобы понять, как он работает.

    > [!NOTE]
    > Можно загрузить рисунок из Интернета путем вставки URL-адреса в диалоговое окно **Открытие файла**. Попробуйте найти изображение с прозрачным фоном, таким образом, чтобы был показан цвет фона.

1. Нажмите кнопку **Очистить рисунок**, чтобы обеспечить удаление рисунка. Затем выйдите из приложения, нажав кнопку **Закрыть**.

## <a name="try-other-features"></a>Изучение других возможностей

* Измените цвет формы и кнопок с помощью свойства **BackColor**.

* Настройте кнопки и флажки с помощью свойств **Font** и **ForeColor**.

* Измените свойства формы **FormBorderStyle** и **ControlBox**.

* Используйте свойства **AcceptButton** и **CancelButton**, чтобы кнопки автоматически нажимались, когда пользователь нажимает клавишу **ВВОД** или **ESC**. Сделайте так, чтобы приложение открывало диалоговое окно **Открытие файла** при нажатии пользователем клавиши **ВВОД** и закрывало окно при нажатии клавиши **ESC**.

## <a name="next-steps"></a>Следующие шаги

Для получения дополнительных сведений перейдите к следующему руководству:

> [!div class="nextstepaction"]
> [Учебник 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md)

Предыдущий раздел руководства: [Шаг 10. Написание кода для дополнительных кнопок и флажка](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>См. также

* [Другие руководства по C#](/visualstudio/get-started/csharp/)
* [Другие руководства по Visual Basic](/visualstudio/get-started/visual-basic/)
* [Руководство по C++](../ide/getting-started-with-cpp-in-visual-studio.md)
