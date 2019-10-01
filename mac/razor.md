---
title: Создание веб-приложений Razor
description: Содержит сведения о поддержке Razor в приложениях ASP.NET Core в Visual Studio для Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: 791182255448db01a1c43796da72bedeec9f2f96
ms.sourcegitcommit: 9a227faafdd0bad6f017ace607dc61eb56b32d72
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/21/2019
ms.locfileid: "71175433"
---
# <a name="create-razor-web-apps"></a>Создание веб-приложений Razor

Из этого руководства вы узнаете, как создать свое первое веб-приложение Razor. Более подробные инструкции см. в статье [Введение в Razor Pages в ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).

Visual Studio для Mac поддерживает редактирование Razor, включая IntelliSense и выделение синтаксиса в файлах *.cshtml*. Начиная с Visual Studio 2019 для Mac версии 8.3 появилась возможность использовать IntelliSense с учетом контекста в файле Razor, что позволяет получать предложения IntelliSense для текущего языка документа.

![Редактирование Razor в Visual Studio для Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Создание нового проекта Razor

1. На экране приветствия выберите **Создать**, чтобы создать проект:

   ![Создание проекта Visual Studio для Mac](media/razor-new.png)
1. В диалоговом окне **Новый проект** выберите **.NET Core** > **Приложение** > **Веб-приложение** и нажмите кнопку **Далее**:

   ![Шаблон проекта Razor](media/razor-new-project1.png)
1. Выберите целевую версию .NET Core (рекомендуется 2.2 или более поздняя) и нажмите кнопку **Далее**. Выберите имя проекта и при необходимости добавьте поддержку Git. Выберите **Создать**, чтобы создать проект.

   ![Имя проекта Razor](media/razor-new-project2.png)

   Visual Studio для Mac откроет проект в окне макета с кодом.
1. Выполните проект без отладки с помощью клавиш **COMMAND+OPTION+F5**.

   Visual Studio запустит [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), откроет в браузере адрес `https://localhost:5001` и отобразит ваше первое веб-приложение Razor.

   ![Веб-приложение Razor в Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Структура проекта

Веб-приложения Razor включают перечисленные ниже компоненты.

### <a name="pages-folder"></a>Папка Pages

В этой папке содержатся веб-страницы проекта, а также код программной части для каждой из них:
* Файл * *.cshtml* для разметки HTML и синтаксиса Razor.
* Файл * *.cshtml.cs* для кода программной части на C#, который обрабатывает события страниц.

Имена вспомогательных файлов начинаются с символа подчеркивания. Например, файл _Layout.cshtml настраивает элементы пользовательского интерфейса, общие для всех страниц. Этот файл настраивает меню навигации в верхней части страницы и уведомление об авторских правах в нижней. Подробные сведения см. в статье [Макет в ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Параметры запуска

Файл *launchSettings.json* содержит параметры IIS, URL-адрес приложения и другие связанные параметры.

### <a name="app-settings"></a>Параметры приложения

Файл *appSettings.json* содержит данные конфигурации, например строки подключения.

Дополнительные сведения о конфигурации см. в статье [Конфигурация в ASP.NET](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Папка wwwroot

Эта папка содержит статические файлы, такие как HTML-файлы, файлы JavaScript и CSS-файлы. Подробные сведения см. в статье [Статические файлы в ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Этот файл содержит точку входа для программы. Подробные сведения см. в статье [Веб-узел ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Этот файл содержит код, который настраивает поведение приложения, например требуется ли согласие для файлов cookie. Подробные сведения см. в статье [Запуск приложения в ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>См. также

Подробное руководство по созданию веб-приложений Razor см. в статье [Введение в Razor Pages в ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).
