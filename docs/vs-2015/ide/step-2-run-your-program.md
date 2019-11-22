---
title: Шаг 2. Запуск программы | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef28781252181dbf765db52dbe6fed1b286516b2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295770"
---
# <a name="step-2-run-your-program"></a>Шаг 2. Запуск программы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании нового решения фактически выполняется построение программы, которая в последующем запускается. Она пока ничего не делает — просто открывает пустое окно, у которого в строке заголовка окна надпись **Form1**. Но, как очевидно, она выполняется.

 ![link to video](../data-tools/media/playvideo.gif "PlayVideo")For a video version of this topic, see [Tutorial 1: Create a Picture Viewer in Visual Basic - Video 1](https://go.microsoft.com/fwlink/?LinkId=205209) or [Tutorial 1: Create a Picture Viewer in C# - Video 1](https://go.microsoft.com/fwlink/?LinkId=205199). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.

### <a name="to-run-your-program"></a>Для запуска программы

1. Для запуска программы используйте один из следующих методов.

    - Нажмите клавишу **F5**.

    - В строке меню выберите **Отладка**, **Начать отладку**.

    - На панели инструментов нажмите кнопку **Начать отладку**, которая показана на рисунке ниже.

         ![Start Debugging toolbar button](../ide/media/express-icondebug.png "Express_IconDebug") Start Debugging toolbar button

2. Visual Studio запускает программу, и открывается окно **Form1**. На следующей диаграмме показана только что созданная программа. Программа выполняется и скоро она будет дополнена.

     ![Windows Form application program running](../ide/media/express-firstrun.png "Express_FirstRun") Windows Form Application program running

3. Вернитесь в интегрированную среду разработки Visual Studio и посмотрите на новую панель инструментов. При запуске программы на панели инструментов появляются дополнительные кнопки. Эти кнопки позволяют выполнять такие действия, как остановка и запуск программы, а также помогают отслеживать все ошибки. В этом примере мы просто используем его для запуска и остановки программы.

     ![Debugging toolbar](../ide/media/express-debugtoolbar.png "Express_DebugToolbar") Debugging toolbar

4. Для остановки программы используйте один из следующих методов.

    - На панели инструментов нажмите кнопку **Остановить отладку**.

    - В строке меню выберите **Отладка**, **Остановить отладку**.

    - Нажмите кнопку X в верхнем углу окна **Form1**.

    > [!NOTE]
    > Когда производится запуск программы внутри интегрированной среды разработки, это называется *отладкой*, так как это обычно выполняется для обнаружения и исправления ошибок в программе. Хотя программа очень мала и пока ничего на самом деле не делает, это все равно настоящая программа. Для запуска и отладки других программ следует выполнить ту же процедуру. Дополнительные сведения об отладке см. в разделе [Основы отладки](../debugger/debugger-basics.md).

### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий шаг руководства см. в разделе [Шаг 3. Задание свойств формы](../ide/step-3-set-your-form-properties.md).

- Предыдущий шаг руководства см. в разделе [Шаг 1. Создание проекта приложения Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md).
