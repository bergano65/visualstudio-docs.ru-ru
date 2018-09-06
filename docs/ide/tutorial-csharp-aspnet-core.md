---
title: Начало работы с C# и ASP.NET Core в Visual Studio
description: Пошаговые инструкции по созданию веб-приложения ASP.NET Core в Visual Studio на C#.
ms.custom: ''
ms.date: 08/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: fb1532a76d9bc530146ba5a0f563bcaa9389226c
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2018
ms.locfileid: "42626989"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Руководство. Начало работы с C# и ASP.NET Core в Visual Studio

В этом руководстве по разработке на языке C# с помощью ASP.NET Core в Visual Studio вы создадите веб-приложение ASP.NET Core на C#, внесете в него изменения, изучите некоторые возможности интегрированной среды разработки и запустите приложение.

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

## <a name="create-a-project"></a>Создание проекта

Сначала создадим проект ASP.NET Core. Для этого типа проекта уже имеются все нужные для веб-сайта файлы шаблонов, что избавляет вас от лишней работы.

1. Откройте Visual Studio 2017.

2. В верхней строке меню выберите **Файл** > **Создать** > **Проект**. 

3. В левой области диалогового окна **Новый проект** разверните узел **Visual C#**, затем разверните узел **Веб** и выберите **.NET Core**. В средней области выберите **Веб-приложение ASP.NET Core**. Назовите файл *MyCoreApp* и нажмите **ОК**.

   ![Шаблон проекта "Веб-приложение ASP.NET Core" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](../ide/media/csharp-aspnet-choose-template-name-mycoreapp-mvc.png)

### <a name="add-a-workload-optional"></a>Добавление рабочей нагрузки (необязательно)

Если шаблон проекта **Веб-приложение ASP.NET Core** отсутствует, его можно получить, добавив рабочую нагрузку **ASP.NET и разработка веб-приложений**. Добавить ее можно одним из двух способов в зависимости от того, какие обновления Visual Studio 2017 установлены на вашем компьютере.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Способ 1. Диалоговое окно "Новый проект"

1. Выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**.

   ![Выберите ссылку "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../ide/media/vs-open-visual-studio-installer-generic.png)

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**, а затем щелкните **Изменить**.

   ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../ide/media/quickstart-aspnet-workload.png)

   (Возможно, перед тем как продолжить установку рабочей нагрузки, придется закрыть Visual Studio.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Способ 2. Меню "Сервис"

1. Закройте диалоговое окно **Создать проект**. Затем в верхней строке меню выберите **Сервис** > **Получить средства и компоненты**.

1. Запускается Visual Studio Installer. Выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**, а затем щелкните **Изменить**.

   (Возможно, перед тем как продолжить установку рабочей нагрузки, придется закрыть Visual Studio.)

### <a name="add-a-project-template"></a>Добавление шаблона проекта

1. В диалоговом окне **Создать веб-приложение ASP.NET Core** выберите шаблон проекта **Веб-приложение (Model-View-Controller)**.

1. Убедитесь, что в верхнем раскрывающемся меню отображается **ASP.NET Core 2.0**. Затем нажмите **ОК**.

   ![Диалоговое окно "Создать веб-приложение ASP.NET Core"](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>Сведения о решении

Это решение строится на основе модели архитектуры MVC, которая разделяет приложение на три основных компонента:

* **Модели** включают в себя классы, представляющие данные приложения. Классы модели используют логику проверки, которая позволяет применять бизнес-правила к этим данным. Как правило, объекты модели извлекают и сохраняют состояние модели в базе данных.
* **Представления** — это компоненты, которые формируют пользовательский интерфейс приложения. Как правило, в пользовательском интерфейсе отображаются данные модели.
* **Контроллеры** включают в себя классы, которые обрабатывают запросы браузера. Они извлекают данные модели и вызывают шаблоны представлений, которые возвращают ответ. В приложении MVC представление служит только для отображения информации. Обработку вводимых данных, реагирование и взаимодействие с пользователем обеспечивает контроллер.

С помощью модели MVC можно создавать приложения, которые тестировать и обновлять удобнее, чем традиционные монолитные приложения.

## <a name="tour-your-solution"></a>Обзор решения

 1. С помощью шаблона проекта создается решение с одним проектом ASP.NET Core, который имеет имя **MyCoreApp**. Разверните узел проекта, чтобы увидеть его содержимое.

    ![Обозреватель решений ASP.NET в Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp-mvc.png)

 1. Откройте файл *HomeController.cs* в папке **Controllers**.

     ![Файл HomeController.cs в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

 1. Просмотрите содержимое файла *HomeController.cs*.

     ![Файл HomeController.cs в окне кода Visual Studio](../ide/media/csharp-aspnet-home-controller-code.png)

 1. Кроме того, проект включает в себя папку **Views**, которая содержит другие папки, соответствующие каждому контроллеру. Например, файл CSHTML (расширение HTML) представления для пути */Home/About* будет находиться по пути *Views/Home/About.cshtml*. Откройте этот файл.

     ![Файл About.cshtml в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

    Этот файл CSHTML использует синтаксис Razor для отрисовки HTML на основе сочетания стандартных тегов и встроенного кода C#.

     ![Файл About.cshtml в окне кода Visual Studio](../ide/media/csharp-aspnet-about-cshtml-code.png)

    >[!NOTE]
    > Дополнительные сведения о Razor см. на странице [Начало работы с C# и ASP.NET с использованием синтаксиса Razor](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

 1. Проект также содержит папку **wwwroot**, которая является корневой для веб-сайта. Разверните папку, чтобы просмотреть его содержимое.

     ![Папка wwwroot в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

    Вы можете поместить статическое содержимое сайта &mdash; например CSS, изображения и библиотеки JavaScript &mdash; непосредственно в нужные пути.

 1. Имеется несколько файлов конфигурации, которые служат для управления проектом, его пакетами и приложением во время выполнения. Например, [конфигурация](/aspnet/core/fundamentals/configuration) приложения по умолчанию хранится в файле *appsettings.json*. Тем не менее эти параметры можно переопределить с помощью *appsettings.Development.json*. Разверните файл **appsettings.json**, чтобы просмотреть файл **appsettings.Development.json**.

     ![Файлы конфигурации в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-debug-and-make-changes"></a>Запуск, отладка и внесение изменений

1. Чтобы выполнить сборку приложения и запустить его в режиме отладки, нажмите в интегрированной среде разработки кнопку **IIS Express**. (Кроме того, можно нажать клавишу **F5** или выбрать пункт меню **Отладка > Начать отладку**.)

     ![Нажмите кнопку "IIS Express" в Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

     > [!NOTE]
     > Если появляется сообщение об ошибке **Не удается подключиться к веб-серверу "IIS Express"**, закройте среду Visual Studio и откройте ее с помощью пункта **Запуск от имени администратора** в контекстном меню. Затем снова запустите приложение.

1. Visual Studio откроет окно браузера. Выберите вкладку **About** (Сведения).

   ![Выбор вкладки "About" в окне браузера с приложением](../ide/media/csharp-aspnet-browser-page.png)

   Помимо прочего, на странице **About** в браузере отображается текст, заданный в файле *HomeController.cs*.

   ![Просмотр текста на странице "About"](../ide/media/csharp-aspnet-browser-page-about.png)

1. Не закрывая окно браузера, вернитесь в Visual Studio. Откройте файл *Controllers/HomeController.cs*, если он еще не открыт.

   ![Открытие файла HomeController.cs в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

1. Установите точку останова в первой строке метода **About**. Для этого щелкните в поле или установите курсор в этой строке и нажмите клавишу **F9**.

   В этой строке задаются данные в коллекции **ViewData**, которые отображаются на CSHTML-странице по пути *Views/Home/About.cshtml*.

   ![Установите точку останова в первой строке метода About в файле About.cshtml.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

1. Вернитесь в браузер и обновите страницу **About**. В Visual Studio будет достигнута точка останова.

1. В Visual Studio наведите указатель на член **ViewData**, чтобы просмотреть его данные.

   ![Просмотр дополнительных сведений о члене ViewData метода About](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

1. Удалите точку останова в приложении, выполнив те же действия, что и для ее добавления.

1. Откройте файл *Views/Home/About.cshtml*.

   ![Выбор файла About.cshtml в обозревателе решений](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

1. Замените слово **additional** на **changed** и сохраните файл.

   ![Замена слова "additional" на "changed"](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

1. Вернитесь в окно браузера, чтобы увидеть новый текст. (Если вы не видите измененный текст, обновите содержимое окна.)

    ![Обновление содержимого окна браузера для отображения измененного текста](../ide/media/csharp-aspnet-browser-page-about-changed.png)

1. Чтобы остановить отладку, на панели инструментов нажмите кнопку **Остановить отладку**. (Кроме того, можно нажать клавишу **SHIFT**+**F5** или выбрать пункт меню **Отладка** > **Остановить отладку**.)

   ![Выберите "Остановить отладку" на панели инструментов](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="quick-answers-faq"></a>Быстрые ответы на часто задаваемые вопросы

Ниже приведен краткий список вопросов и ответов, с помощью которого вы сможете ознакомиться с некоторыми основными понятиями.

### <a name="what-is-c"></a>Что такое C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) — это типобезопасный объектно-ориентированный язык программирования, который обладает широкими возможностями, но в то же время прост в обучении.

### <a name="what-is-aspnet-core"></a>Что такое ASP.NET Core?

ASP.NET Core — это кроссплатформенная платформа с открытым кодом для создания приложений, подключенных к Интернету, таких как веб-приложения и службы. Приложения ASP.NET Core могут работать на основе .NET Core или .NET Framework. Приложения ASP.NET Core можно разрабатывать и запускать на различных платформах, включая Windows, Mac и Linux. Код ASP.NET Core открыт для общего доступа в [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Что такое Visual Studio?

Visual Studio — это интегрированный набор средств разработки. Его можно рассматривать как программу для создания приложений.

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого учебника! Надеемся, что вы узнали что-то новое о C#, ASP.NET Core и интегрированной среде разработки Visual Studio. Дополнительные сведения о создании веб-приложения или веб-сайта с помощью C# и ASP.NET вы найдете в следующих руководствах:

> [!div class="nextstepaction"]
> [Создание веб-приложения MVC с помощью ASP.NET Core](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x)
>
> [!div class="nextstepaction"]
> [Создание веб-приложения Razor Pages с помощью ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>См. также

[Публикация веб-приложения в службе приложений Azure с помощью Visual Studio](..//deployment/quickstart-deploy-to-azure.md)