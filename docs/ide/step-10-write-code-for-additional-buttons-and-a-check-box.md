---
title: Шаг 10. Написание кода дополнительных кнопок и флажка
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a5b7fa7291def4a988d268eebdf9bf5e96c7f7b
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747763"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Шаг 10. Написание кода дополнительных кнопок и флажка
Теперь можно завершить другие четыре метода. Можно копировать и вставить этот код, но для получения дополнительных навыков введите код и используйте IntelliSense.

 Этот код добавляет функциональность к ранее добавленным кнопкам. Без этого кода кнопки ничего не делают. Код используется в событиях <xref:System.Windows.Forms.Control.Click> кнопок (в случае флажка это событие <xref:System.Windows.Forms.CheckBox.CheckedChanged>) для выполнения различных действий при активации пользователем этих элементов управления. Например, событие `clearButton_Click`, которое активируется при нажатии кнопки **Очистить рисунок**, удаляет текущее изображение, задав его свойству **Image** значение **null** (или **nothing**). Каждое событие в коде сопровождается комментариями, которые поясняют, что делает код.

 ![ссылка на видео](../data-tools/media/playvideo.gif)Видеоверсию этой статьи см. на следующих страницах: [Руководство 1. Создание приложения для просмотра рисунков на Visual Basic — видео 5](http://go.microsoft.com/fwlink/?LinkId=205216) и [Руководство 1. Создание приложения для просмотра рисунков на C# — видео 5](http://go.microsoft.com/fwlink/?LinkId=205206). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.

> [!NOTE]
>  Рекомендация — всегда снабжайте код комментариями. Комментарии — это сведения для человека, который читает код, необходимы для того, чтобы сделать код понятным. Содержимое в строке комментария игнорируется программой. В Visual C# строка комментария начинается с двух символов косой черты (//), в Visual Basic строка комментария начинается с одного знака одинарной кавычки (').

## <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Написание кода для дополнительных кнопок и флажка

-   Добавьте следующий код в файл кода **Form1** (*Form1.cs* или *Form1.vb*). Перейдите на вкладку **VB** для просмотра Visual Basic-версии кода.

     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

-   Следующий раздел: [Шаг 11. Запуск программы и изучение других возможностей](../ide/step-11-run-your-program-and-try-other-features.md).

-   Предыдущий раздел: [Шаг 9. Проверка, комментирование и тестирование кода](../ide/step-9-review-comment-and-test-your-code.md).
