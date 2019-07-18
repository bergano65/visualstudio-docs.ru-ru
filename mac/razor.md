---
title: Razor
description: Сведения о поддержке razor в приложениях asp.net core в Visual Studio для Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: 9e5a3f61ee7065a0615a381bdcc03dafc3566893
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691270"
---
# <a name="razor"></a>Razor

Visual Studio для Mac поддерживает редактирование Razor, включая IntelliSense и выделение синтаксиса в файлах *.cshtml*.

![Редактирование Razor в Visual Studio для Mac](media/razor-editor.png)

Из этого руководства вы узнаете, как создать свое первое веб-приложение Razor. Подробные сведения см. в [документации по Razor Pages в .NET Core](/aspnet/core/razor-pages/index).

## <a name="creating-a-new-razor-project"></a>Создание нового проекта Razor

* На экране приветствия выберите **New** (Создать), чтобы создать новый проект:

![Создание проекта Visual Studio для Mac](media/razor-new.png)

* В диалоговом окне New Project (Новый проект) выберите **.NET Core** > **App** (Приложение) > **Web Application** (Веб-приложение) и нажмите кнопку **Далее**:

![Шаблон проекта Razor](media/razor-new-project1.png)

* Выберите требуемую версию .NET Core (рекомендуется 2.2 или выше) и нажмите кнопку **Далее**.  Выберите имя проекта и при необходимости добавьте поддержку git. Выберите **Создать**, чтобы создать проект.

![Имя проекта Razor](media/razor-new-project2.png)

Visual Studio для Mac откроет проект в макете с кодом.

* Выполните проект без запуска отладки с помощью клавиш **CMD+OPT+F5**

Visual Studio запустит [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) и откроет браузер с переходом по адресу `https://localhost:5001` и отображением вашего первого веб-приложения Razor:

![Веб-приложение Razor в Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Структура проекта

Веб-приложения Razor включают следующие компоненты:

### <a name="pages-folder"></a>Папка Pages

В папке Pages в проекте можно найти веб-страницы, а также код программной части для каждой из них:
* Файл * *.cshtml* для разметки HTML и синтаксиса Razor.
* Файл * *.cshtml.cs* для кода программной части на C#, который обрабатывает события страниц.

Имена вспомогательных файлов начинаются с символа подчеркивания. Например, файл _Layout.cshtml настраивает элементы пользовательского интерфейса, общие для всех страниц. Этот файл настраивает меню навигации в верхней части страницы и уведомление об авторских правах в нижней части страницы. Подробные сведения см. в статье [Макет в ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Параметры запуска

Файл *launchSettings.json* содержит параметры IIS, URL-адрес приложения и другие связанные параметры.

### <a name="app-settings"></a>Параметры приложения

Файл *appSettings.json* содержит данные конфигурации, например строки подключений.

Подробные сведения о конфигурации см. в статье [Конфигурация в .NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Папка wwwroot

Содержит статические файлы, такие как HTML-файлы, файлы JavaScript и CSS-файлы. Подробные сведения см. в статье [Статические файлы в ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Содержит точку входа для программы. Подробные сведения см. в статье [Веб-узел ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Содержит код, который настраивает поведение приложения, например, требуется ли согласие для файлов cookie. Подробные сведения см. в статье [Запуск приложения в ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-aso"></a>Дополнительные материалы

Подробное руководство по созданию веб-приложений Razor см. в статье [Введение в Razor Pages в ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).
