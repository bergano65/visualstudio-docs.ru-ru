---
title: Создание веб-приложений Blazor
description: Содержит сведения о поддержке Blazor в приложениях ASP.NET Core в Visual Studio для Mac.
author: jongalloway
ms.author: jogallow
ms.date: 08/31/2020
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 30e9a62e8bf0364a76cbd43995cbb77c1a5bd0c4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729422"
---
# <a name="create-blazor-web-apps"></a>Создание веб-приложений Blazor

Из этого руководства вы узнаете, как создать свое первое веб-приложение Blazor. Более подробные инструкции см. в статье [Введение в ASP.NET Core Blazor](/aspnet/core/blazor/index).

ASP.NET Core Blazor поддерживает два разных варианта размещения: Blazor WebAssembly (WASM) и Blazor Server. Visual Studio для Mac поддерживает обе модели размещения. Visual Studio для Mac начиная с версии 8.4 поддерживает Blazor Server, а начиная с версии 8.6 — оба варианта. Дополнительные сведения о моделях размещения Blazor см. в статье [Модели размещения ASP.NET Core Blazor](/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1&preserve-view=true). Поддержка отладки проектов Blazor WebAssembly в Visual Studio для Mac доступна в предварительной версии выпуска 8.8 (предоставляется через канал обновления предварительной версии в меню **Visual Studio > Проверить обновления...** ).

Что такое Blazor? Blazor — это платформа для создания интерактивных клиентских веб-интерфейсов на основе .NET, которая предоставляет веб-разработчикам следующие преимущества:

* создание кода на C#, а не на JavaScript;
* возможность использования существующей экосистемы .NET с библиотеками .NET;
* сохранение единой логики приложений для сервера и клиента;
* высокая производительность, надежность и безопасность платформы .NET;
* возможность сохранения высокого уровня продуктивности с помощью Visual Studio в Windows, Linux и macOS;
* создание приложений на основе распространенных языков, платформ и инструментов, которые отличаются стабильностью, широким набором функций и простотой в использовании.

## <a name="create-a-new-blazor-webassembly-project"></a>Создание нового проекта Blazor WebAssembly
1. В **окне запуска** выберите **Новый**, чтобы создать проект:

   ![Окно запуска Visual Studio для Mac с выделенным параметром "Создать"](media/blazor-new-project.png)

1. В диалоговом окне **Новый проект** выберите **.NET Core** > **Приложение** > **Приложение Blazor WebAssembly** и щелкните **Далее**. ![Снимок экрана: диалоговое окно нового проекта с Blazor WebAssembly Приложение, выделенное в области "Приложение" в разделе "ASP.NET Core", и нажатая кнопка "Далее".](media/blazor-wasm-project-template.png)

1. Выберите .NET Core 3.1 в качестве целевой платформы, а затем нажмите кнопку **Далее**. 
   ![Диалоговое окно настройки нового приложения Blazor WebAssembly с выбранной целевой платформой .NET Core 3.1](media/blazor-wasm-select-target-framework.png)

1. Выберите имя проекта и при необходимости добавьте поддержку Git. Выберите **Создать**, чтобы создать проект.
    ![Диалоговое окно настройки нового приложения Blazor WebAssembly с вводимым именем проекта](media/blazor-wasm-name-project.png)

   Visual Studio для Mac откроет проект в окне макета с кодом.

1. Выберите **Выполнить** > **Запуск без отладки**, чтобы запустить приложение.

   Visual Studio запустит [Kestrel](/aspnet/core/fundamentals/servers/kestrel), откроет в браузере адрес `https://localhost:5001` и отобразит ваше веб-приложение Blazor.

   ![Веб-приложение Blazor в Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="creating-a-new-blazor-server-project"></a>Создание проекта Blazor Server

1. В **окне запуска** выберите **Новый**, чтобы создать проект:

   ![Окно запуска Visual Studio для Mac с выделенным параметром "Создать"](media/blazor-new-project.png)
1. В диалоговом окне **Новый проект** выберите **.NET Core** > **Приложение** > **Серверное приложение Blazor** , а затем выберите **Далее**. ![Снимок экрана: диалоговое окно нового проекта с Blazor Приложение Server, выделенное в области "Приложение" в разделе "ASP.NET Core", и нажатая кнопка "Далее".](media/blazor-project-template.png)

1. Выберите .NET Core 3.1 в качестве целевой платформы, а затем нажмите кнопку **Далее**. 
   ![Настройте новое диалоговое окно серверного приложения Blazor с выбранной целевой платформой .NET Core 3.1](media/blazor-select-target-framework.png)

1. Выберите имя проекта и при необходимости добавьте поддержку Git. Выберите **Создать**, чтобы создать проект.
   ![Настройте новое диалоговое окно серверного приложения Blazor отображаемое при вводе имени проекта](media/blazor-name-project.png)

   Visual Studio для Mac откроет проект в окне макета с кодом.
1. Выберите **Выполнить** > **Запуск без отладки**, чтобы запустить приложение.

   Visual Studio запустит [Kestrel](/aspnet/core/fundamentals/servers/kestrel), откроет в браузере адрес `https://localhost:5001` и отобразит ваше веб-приложение Blazor.

   ![Веб-приложение Blazor в Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Поддержка Blazor в Visual Studio для Mac

Visual Studio для Mac (начиная с версии 8.4) включает новые функции для создания серверных проектов Blazor. Кроме того, эта среда предоставляет стандартную поддержку, охватывающую создание, запуск и отладку проектов Blazor. В Visual Studio для Mac 8.6 была добавлена поддержка создания, сборки и запуска проектов Blazor WebAssembly.

В приведенном выше пошаговом руководстве показано, как использовать шаблон проекта приложения Blazor Server для создания нового приложения Blazor Server или проекта приложения Blazor WebAssembly. Рассмотрим некоторые дополнительные функции Visual Studio для Mac для поддержки разработки проектов Blazor.

### <a name="editor-support-for-razor-files"></a>Поддержка редактора *RAZOR*-файлов
В Visual Studio для Mac можно редактировать RAZOR-файлы — это большая часть файлов, которые будут использоваться при создании приложений Blazor. В Visual Studio для Mac реализована полная поддержка выделения цветом и выполнения кода из RAZOR-файлов, включая выполнение для компонентов Razor, объявленных в проекте.

![Окно редактора Visual Studio для Mac с Intellisense для Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Публикация приложений Blazor в Службе приложений Azure
Вы также можете публиковать приложения Blazor непосредственно в Службе приложений Azure. Если у вас нет учетной записи Azure для запуска приложения Blazor в Azure, вы можете [бесплатно зарегистрироваться](https://azure.microsoft.com/free) и использовать популярные службы в течение 12 месяцев без оплаты. Вы также получите 200 долл. США на счет в Azure и возможность бесплатно работать более чем с 25 службами.

![Диалоговое окно Visual Studio для Mac с параметром публикации в Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Структура проекта

По умолчанию веб-приложения Blazor включают несколько каталогов и файлов. Перед началом работы необходимо ознакомиться с основными из них.

### <a name="pages-folder"></a>Папка Pages

Эта папка содержит веб-страницы проекта с расширением файла *RAZOR*.

### <a name="shared-folder"></a>Папка Shared

Эта папка содержит общие компоненты с расширением *RAZOR*. Сюда входит файл *MainLayout.razor*, который используется для определения общих макетов в приложении. Она также содержит компонент *NavMenu.razor*, используемый на всех страницах. Если вы создаете многократно используемые компоненты, они попадут в папку **Shared**.

### <a name="app-settings"></a>Параметры приложения

Файл *appSettings.json* содержит данные конфигурации, например строки подключения.

Дополнительные сведения о конфигурации см. в статье [Конфигурация в ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Папка wwwroot

Эта папка содержит статические файлы, такие как HTML-файлы, файлы JavaScript и CSS-файлы. Подробные сведения см. в статье [Статические файлы в ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Этот файл содержит точку входа для программы. Подробные сведения см. в статье [Веб-узел ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="blazor-server-app-specific-files"></a>Файлы, относящиеся к приложению Blazor Server
#### <a name="app-settings"></a>Параметры приложения

Файл *appSettings.json* содержит данные конфигурации, например строки подключения.

Дополнительные сведения о конфигурации см. в статье [Конфигурация в ASP.NET](/aspnet/core/fundamentals/configuration/index).

#### <a name="startupcs"></a>Startup.cs

Этот файл содержит код, который настраивает поведение приложения, например требуется ли согласие для файлов cookie. Подробные сведения см. в статье [Запуск приложения в ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Сводка
Из этого руководства вы узнали, как создать приложение Blazor Server или приложение Blazor WebAssembly в Visual Studio для Mac, и получили сведения о некоторых функциях Visual Studio для Mac, которые помогают создавать приложения Blazor.

## <a name="see-also"></a>См. также

Более подробное руководство по созданию веб-приложений Blazor см. в статье [Введение в ASP.NET Core Blazor](/aspnet/core/blazor/index).