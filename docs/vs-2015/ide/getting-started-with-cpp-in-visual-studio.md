---
title: Начало работы с C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 264fcea4b04b1777a455199789ed1bb9c3757f7c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758246"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Начало работы с C++ в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Выполнив это пошаговое руководство, вы ознакомитесь со многими инструментами и диалоговыми окнами, которые можно использовать для разработки приложений с помощью Visual Studio. Вы создадите простое приложение в стиле Hello, World, чтобы глубже изучить работу в интегрированной среде разработки (IDE).

 В этом разделе содержатся следующие подразделы.

 [Вход в Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Создание простого приложения](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Добавление кода в приложение](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Отладка и тестирование приложения](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Сборка окончательной версии приложения](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

##  <a name="BKMK_Configure"></a> Вход в Visual Studio
 При первом запуске Visual Studio предоставляется возможность выполнить вход с использованием учетной записи Майкрософт, например Live или Outlook. Вход позволяет обеспечить синхронизацию пользовательских параметров на всех устройствах. Дополнительные сведения см. в разделе [Signing in to Visual Studio](../ide/signing-in-to-visual-studio.md).

 Рисунок 1. Интегрированная среда разработки Visual Studio

 ![Интегрированная среда разработки с примененными параметрами Visual C++](../ide/media/c-ide-defaultenvironmentlayout.png "C++IDE_DefaultEnvironmentLayout")

 После открытия Visual Studio можно увидеть три основные части интегрированной среды разработки: окна инструментов, меню с панелями инструментов и область главного окна. Окна инструментов закреплены в левой и правой частях окна приложения, а панель **Быстрый запуск**, строка меню и стандартная панель инструментов закреплены в его верхней части. В центре окна приложения находится **Начальная страница**. При открытии решения или проекта редакторы и конструкторы отображаются в этом пространстве. При разработке приложения чаще всего используется именно эта область.

##  <a name="BKMK_CreateApp"></a> Создание простого приложения
 При создании приложения в Visual Studio необходимо сначала создать проект и решение. В этом примере создается консольное приложение Windows.

#### <a name="to-create-a-console-app"></a>Создание консольного приложения

1. В строке меню выберите **Файл**, **Создать**, **Проект**.

    ![Выбор пунктов "Файл", "Создать", "Проект"](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. В категории **Visual C++** выберите шаблон **Консольное приложение Win32** и назовите проект `GreetingsConsoleApp`.

    ![Шаблон консольного приложения Win32](../ide/media/c-ide-newprojectdlg.png "C++IDE_NewProjectDlg")

3. Когда появится мастер приложений Win32, нажмите кнопку **Готово** .

    ![Мастер консольного приложения Win32](../ide/media/c-ide-win32consoleappwizard.png "C++IDE_Win32ConsoleAppWizard")

   Проект GreetingsConsoleApp и решение с основными файлами для консольного приложения Win32 создадутся и автоматически загрузятся в **Обозреватель решений**. Файл GreettingsConsoleApp.cpp откроется в редакторе кода. В **Обозревателе решений**отображаются следующие элементы.

   Рисунок 4. Элементы проекта

   ![Файлы для решения в обозревателе решений](../ide/media/c-ide-solutioncontents.png "C++IDE_SolutionContents")

##  <a name="BKMK_AddCode"></a> Добавление кода в приложение
 Далее необходимо добавить код для отображения слова "Hello" в окне консоли.

#### <a name="to-display-hello-in-the-console-window"></a>Отображение "Hello" в окне консоли

1.  В файле GreetingsConsoleApp.cpp введите пустую строку перед строкой `return 0;` , а затем введите в нее следующий код:

    ```
    cout << "Hello\n";
    ```

     Красная волнистая линия появится под `cout`. При наведении на нее отобразится сообщение об ошибке.

     ![Текст сообщения об ошибке для cout](../ide/media/c-ide-couterror.png "C++IDE_CoutError")

     Сообщение об ошибке также отобразится в окне **Список ошибок** . Можно отобразить это окно, выбрав в строке меню **Вид**, **Список ошибок**.

     [cout](http://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) включается в файл заголовка \<iostream\>.

2.  Для включения заголовка iostream введите следующий код после `#include "stdafx.h"`:

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Возможно, вы заметили, что после вставки этого кода появилось окно, предлагающее рекомендации для символов, которые были введены. Это поле является частью технологии C++ IntelliSense, обеспечивающей подсказки по коду, в том числе отображение членов класса или интерфейса и сведения о параметрах. Кроме того, можно использовать фрагменты кода в виде предопределенных блоков кода. Дополнительные сведения см. в разделах [Using IntelliSense](../ide/using-intellisense.md) и [Code Snippets](../ide/code-snippets.md).

     Красная волнистая линия под `cout` исчезнет после исправления ошибки.

3.  Сохраните изменения в файле.

     ![Код, исправляющий ошибку cout](../ide/media/c-ide-coutfix.png "C++IDE_CoutFix")

##  <a name="BKMK_DebugTest"></a> Отладка и тестирование приложения
 С помощью отладки GreetingsConsoleApp можно посмотреть, отображается ли слово Hello в окне консоли.

#### <a name="to-debug-the-application"></a>Отладка приложения

-   Запустите отладчик.

     ![Команда "Начать отладку" в меню "Отладка"](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")

     Отладчик запустится и выполнит код. Окно консоли (отдельное окно, подобное командной строке) отображается в течение нескольких секунд, но при остановке отладчика быстро закрывается. Чтобы просмотреть текст, необходимо установить точку останова выполнения программы.

#### <a name="to-add-a-breakpoint"></a>Добавление точки останова

1. Добавьте точку останова из меню в строке `return 0;`. Для установки точки останова можно также просто щелкнуть область слева.

    ![Команда "Точка останова" в меню "Отладка"](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE-ToggleBreakpoint")

    Рядом со строкой кода в крайнем левом поле окна редактора появится красный кружок.

2. Нажмите клавишу F5, чтобы начать отладку.

    Запускается отладчик, и появляется окно консоли, в котором выводится слово **Hello**.

    ![Текст "Hello" в окне командной строки Windows](../ide/media/c-ide-hellocommandwindow.png "C++IDE_HelloCommandWindow")

3. Для останова процесса отладки нажмите SHIFT + F5.

   Дополнительные сведения см. в статье [Консольные проекты](../debugger/debugging-preparation-console-projects.md).

##  <a name="BKMK_BuildRelease"></a> Сборка окончательной версии приложения
 Теперь, когда вы проверили, что все работает, можно подготовить окончательную сборку приложения.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Очистка файлов решения и сборка окончательной версии

1. Из строки меню удалите промежуточные файлы и выходные файлы, созданные во время предыдущих сборок.

    ![Команда "Очистить решение" в меню "Сборка"](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")

2. Измените конфигурацию сборки для GreetingsConsoleApp с **Отладка** на **Выпуск**.

    ![Сборка окончательной версии приложения](../ide/media/c-ide-changingbuildtorelease.png "C++IDE_ChangingBuildtoRelease")

3. Постройте решение.

    ![Команда "Собрать решение" в меню "Сборка"](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Поздравляем с завершением этого пошагового руководства! Чтобы изучить больше примеров, см. раздел [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>См. также раздел
 [Пошаговое руководство: Создание простого приложения](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [советы по повышению производительности](../ide/productivity-tips-for-visual-studio.md) [примеры Visual Studio](../ide/visual-studio-samples.md) [начало разработки в Visual Studio](../ide/get-started-developing-with-visual-studio.md)
