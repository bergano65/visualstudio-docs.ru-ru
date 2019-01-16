---
title: Обучающие проекты и решения для Visual Basic
ms.date: 12/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9d3196a1e6828d093245043ec5c21accd50a6bbb
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739621"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Сведения о проектах и решениях с использованием Visual Basic

В этой вводной статье мы изучим, что означает создание *решения* и *проекта* в Visual Studio. Решение — это контейнер, который используется для упорядочения одного или нескольких связанных проектов, например проекта библиотеки классов и соответствующего тестового проекта. Мы рассмотрим свойства проекта, а также некоторые файлы, которые он может содержать. Мы также создадим ссылку из одного проекта в другой.

> [!TIP]
> Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

В качестве упражнения мы создадим решение и проект с нуля, чтобы понять концепцию проекта. В повседневной работе с Visual Studio вы, скорее всего, будете использовать для создания проекта различные *шаблоны*, доступные в Visual Studio.

> [!NOTE]
> Для разработки приложений в Visual Studio необязательно использовать проекты и решения. Вы можете просто открыть папку, содержащую код, и начать написание кода, сборку и отладку. Например, если вы клонируете репозиторий [GitHub](https://github.com/), он может не содержать проекты и решения Visual Studio. Дополнительные сведения см. в статье [Разработка кода в Visual Studio без использования проектов и решений](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Проекты и решения

Несмотря на название, под решением не подразумевается "решение вопроса". Решения — это просто контейнеры, используемые Visual Studio для упорядочения одного или нескольких связанных проектов. Когда вы открываете решение в среде Visual Studio, все содержащиеся в нем проекты загружаются автоматически.

### <a name="create-a-solution"></a>Создание решения

Обучение мы начнем с создания пустого решения. Когда вы научитесь работать в Visual Studio, скорее всего, создавать пустые решения вам потребуется не слишком часто. При создании проекта в среде Visual Studio она автоматически создает решение для размещения проекта, если никакое решение еще не открыто.

1. Запустите Visual Studio.

1. В строке меню, где расположены разделы **Файл** и **Изменить**, выберите **Файл** > **Создать** > **Проект**.

   Откроется диалоговое окно **Новый проект** .

1. В левой области разверните узел **Другие типы проектов** и выберите **Решения Visual Studio**. На центральной панели выберите шаблон **Пустое решение**. Назовите решение **QuickSolution** и нажмите кнопку **ОК**.

   ![Шаблон пустого решения в Visual Studio](../media/tutorial-projects-new-solution.png)

   **Начальная страница** закрывается, а решение отображается в **обозревателе решений** в правой части окна Visual Studio. Вероятнее всего, вы довольно часто будете использовать **обозреватель решений** для просмотра содержимого проектов.

### <a name="add-a-project"></a>Добавление проекта

А теперь давайте добавим первый проект в это решение. Мы начнем с пустого проекта и добавим в него нужные элементы.

1. В контекстном меню, вызываемом щелчком правой кнопкой мыши элемента **Решение "QuickSolution"** в **обозревателе решений**, выберите пункты **Добавить** > **Создать проект**.

   Откроется диалоговое окно **Добавить новый проект** .

1. В левой области разверните узел **Visual Basic** и выберите пункт **Рабочий стол Windows**. После этого в средней области выберите шаблон **Пустой проект (.NET Framework)**. Назовите проект **QuickDate** и нажмите кнопку **OK**.

   Проект с именем "QuickDate" появляется под решением в **обозревателе решений**. Сейчас он содержит один файл с именем *App.config*.

   > [!NOTE]
   > Если вы не видите **Visual Basic** в левой области диалогового окна, нужно установить *рабочую нагрузку* Visual Studio **Разработка классических приложений .NET**. Visual Studio использует установку на основе рабочей нагрузки, чтобы устанавливать только те компоненты, которые необходимы для этого типа разработки. Чтобы установить рабочую нагрузку, просто нажмите на ссылку **Открыть Visual Studio Installer** в левом нижнем углу диалогового окна **Добавить новый проект**. После запуска Visual Studio Installer выберите рабочую нагрузку **Разработка классических приложений .NET** и нажмите кнопу **Изменить**.

   ![Ссылка "Открыть Visual Studio Installer"](media/tutorial-projects-open-installer-vb.png)

## <a name="add-an-item-to-the-project"></a>Добавление элемента в проект

У нас есть пустой проект. Давайте добавим файл кода.

1. В контекстном меню, вызываемом щелчком правой кнопкой мыши на проекте **QuickDate** в **обозревателе решений**, выберите пункты **Добавить** > **Создать элемент**.

   Откроется диалоговое окно **Добавление нового элемента**.

1. Разверните узел **Общие элементы** и выберите **Код**. В средней области выберите шаблон элемента **Класс**. Задайте для класса имя **Calendar** и нажмите кнопку **Добавить**.

   В проект добавляется файл *Calendar.vb*. Расширение *VB* присваивается файлам кода Visual Basic. Этот файл появляется в иерархии проекта в **обозревателе решений**, а его содержимое открывается в редакторе.

1. Замените содержимое файла *Calendar.vb* приведенным ниже кодом:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   Класс `Calendar` содержит одну функцию `GetCurrentDate`, которая возвращает текущую дату.

1. Откройте свойства проекта, дважды щелкнув **Мой проект** в **обозревателе решений**. На вкладке **Приложения** для параметра **Тип приложения** выберите значение **Библиотека классов**. Этот шаг необходим для успешной сборки проекта.

1. Выполните сборку, щелкнув правой кнопкой мыши элемент **QuickDate** в **обозревателе решений** и выбрав команду **Сборка**. В окне **вывода** появится сообщение об успешном выполнении сборки.

## <a name="add-a-second-project"></a>Добавление второго проекта

Чаще всего решения содержат несколько проектов, которые ссылаются друг на друга. Некоторые проекты в решении могут быть библиотеками классов, некоторые — исполняемыми приложениями, а другие — проектами модульных тестов или веб-сайтами.

Давайте добавим в решение проект модульного теста. В этот раз мы начнем с шаблона проекта, поэтому нам не нужно добавлять в проект дополнительный файл кода.

1. В контекстном меню, вызываемом щелчком правой кнопкой мыши элемента **Решение "QuickSolution"** в **обозревателе решений**, выберите пункты **Добавить** > **Создать проект**.

   Откроется диалоговое окно **Добавить новый проект** .

1. В левой области разверните узел **Visual Basic** и выберите категорию **Тест**. В средней области выберите шаблон проекта **Проект модульного теста (.NET Framework)**. Укажите **QuickTest** в качестве имени проекта и нажмите кнопку **ОК**.

   Второй проект добавляется в **обозреватель решений**, а файл с именем *UnitTest1.vb* открывается в редакторе.

   ![Обозреватель решений Visual Studio с двумя проектами](media/tutorial-projects-solution-explorer-vb.png)

## <a name="add-a-project-reference"></a>Добавление ссылки на проект

Мы будем использовать новый проект модульного теста для тестирования своего метода в проекте **QuickDate**, поэтому нужно добавить ссылку на этот проект. Это создает *зависимость сборки* между двумя проектами, то есть **QuickDate** будет собран перед **QuickTest** при сборке решения.

1. Выберите узел **Ссылки** в проекте **QuickTest**, а затем в контекстном меню выберите пункт **Добавить ссылку**.

   ![Меню "Добавление ссылки"](media/tutorial-projects-add-reference-vb.png)

   Открывается диалоговое окно **Диспетчер ссылок**.

1. В левой области разверните узел **Проекты** и выберите **Решение**. В средней области установите флажок рядом с пунктом **QuickDate** и нажмите кнопку **ОК**.

   Добавляется ссылка на проект **QuickDate**.

## <a name="add-test-code"></a>Добавление кода теста

1. Теперь мы добавим код теста в файл кода Visual Basic. Замените все содержимое файла *UnitTest1.vb* приведенным ниже кодом.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Вы увидите под некоторым кодом красную волнистую линию. Мы устраним эту ошибку, сделав тестовый проект [дружественной сборкой](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) для проекта **QuickDate**.

1. В проекте **QuickDate** откройте файл *Calendar.vb*, если он еще не открыт, и добавьте указанный ниже [оператор Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) и атрибут <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> для устранения ошибки в тестовом проекте.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Файл кода должен выглядеть следующим образом:

   ![код Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Свойства проекта

Строка в файле *Calendar.vb*, содержащая атрибут <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, ссылается на имя сборки (имя файла) проекта **QuickTest**. Имя сборки может не всегда совпадать с именем проекта. Чтобы найти имя сборки проекта, откройте свойства проекта.

1. Выберите проект **QuickTest** в **обозревателе решений**. Выберите **Свойства**  в контекстном меню или просто нажмите клавиши **ALT**+**ВВОД**. (Также можно дважды щелкнуть **Мой проект** в окне **обозревателя решений**.)

   *Страницы свойств* для проекта, открытые на вкладке **Приложение**. Страницы свойств содержат различные параметры для проекта. Обратите внимание, что имя сборки проекта **QuickTest** действительно имеет значение "QuickTest". Если вы хотите изменить его, это можно сделать здесь. Позже, при сборке тестового проекта, имя итогового двоичного файла изменится с *QuickTest.dll* на то, которое вы выбрали.

   ![Свойства проекта](../media/tutorial-projects-properties.png)

1. Изучите другие вкладки на страницах свойств, такие как **Компиляция** и **Параметры**. Эти вкладки отличаются для различных типов проектов.

## <a name="optional-run-the-test"></a>Запуск теста (необязательно)

Если вы хотите проверить работоспособность модульного теста, выберите **Тест** > **Запуск** > **Все тесты** в строке меню. Открывается окно **Обозреватель тестов**, где должно быть указано, что тест **TestGetCurrentDate** пройден.

![Team Explorer в Visual Studio отображает пройденный тест.](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Если **Обозреватель тестов** не открывается автоматически, выберите в строке меню **Тест** > **Windows** > **Обозреватель тестов**.

## <a name="next-steps"></a>Следующие шаги

Если вы хотите более детально изучить Visual Studio, попробуйте создать приложение по любому из [руководств по Visual Basic](index.yml).

## <a name="see-also"></a>См. также

- [Создание проектов и решений](../../ide/creating-solutions-and-projects.md)
- [Управление свойствами проектов и решений](../../ide/managing-project-and-solution-properties.md)
- [Управление ссылками в проекте](../../ide/managing-references-in-a-project.md)
- [Разработка кода в Visual Studio без использования проектов и решений](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Обзор интегрированной среды разработки Visual Studio](../../get-started/visual-studio-ide.md)