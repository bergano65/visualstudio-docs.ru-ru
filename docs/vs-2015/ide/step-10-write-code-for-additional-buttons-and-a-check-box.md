---
title: Шаг 10. Написание кода дополнительных кнопок и флажка | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24152bf2e6acfcb1ed20b75a5c817e0336cdd4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851592"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Шаг 10. Написание кода дополнительных кнопок и флажка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Теперь можно завершить другие четыре метода. Можно копировать и вставить этот код, но для получения дополнительных навыков введите код и используйте IntelliSense.

 Этот код добавляет функциональность к ранее добавленным кнопкам. Без этого кода кнопки ничего не делают. Код используется в событиях `Click` кнопок (в случае флажка это событие `CheckChanged`) для выполнения различных действий при активации пользователем этих элементов управления. Например, событие `clearButton_Click`, которое активируется при нажатии кнопки **Очистить рисунок**, удаляет текущее изображение, установив его свойству `Image` значение `null` (или `nothing`). Каждое событие в коде сопровождается комментариями, которые поясняют, что делает код.

 ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") Для получения видео-версии этой статьи см. [руководство 1. Создание средства просмотра изображений в Visual Basic-Video 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) или [учебном курсе 1. Создание средства просмотра изображений на C# — видео 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.

> [!NOTE]
> Рекомендация — всегда снабжайте код комментариями. Комментарии — это сведения для человека, который читает код, необходимы для того, чтобы сделать код понятным. Содержимое в строке комментария игнорируется программой. В Visual C# строка комментария начинается с двух символов косой черты (//), в Visual Basic строка комментария начинается с одного знака одинарной кавычки (').

### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Написание кода для дополнительных кнопок и флажка

- Добавьте следующий код в файл кода Form1 (Form1.cs или Form1.vb). Перейдите на вкладку **VB** для просмотра Visual Basic-версии кода.

     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]

### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий шаг руководства см. в разделе [Шаг 11. Запуск программы и изучение других возможностей](../ide/step-11-run-your-program-and-try-other-features.md).

- Чтобы вернуться к предыдущему шагу руководства, см. [Шаг 9. Просмотр, комментирование и тестирование кода](../ide/step-9-review-comment-and-test-your-code.md).
