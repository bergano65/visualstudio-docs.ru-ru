---
title: Публикация в IIS посредством импорта параметров публикации
description: Создание и импорт профиля публикации для развертывания приложения из Visual Studio в IIS
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13a4210e24fe64db79be897bc159477e9b2f5a3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53897390"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Публикация приложения в IIS посредством импорта параметров публикации в Visual Studio

Вы можете использовать средство **публикации** для импорта параметров публикации, а затем развернуть приложение. В этой статье мы используем параметры публикации для IIS, однако аналогичные действия можно использовать, чтобы импортировать параметры публикации для [Службы приложений Azure](../deployment/tutorial-import-publish-settings-azure.md). В некоторых случаях использование профиля параметров публикации может оказаться быстрее, чем ручная настройка развертывания в IIS для каждой установки Visual Studio.

Эти шаги применимы к приложениям ASP.NET, ASP.NET Core и .NET Core в Visual Studio. Эти действия соответствуют Visual Studio 2017 версии 15.6.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Настройка IIS таким образом, чтобы вы могли создать файл параметров публикации.
> * Создание файла параметров публикации.
> * Импорт файла параметров публикации в Visual Studio.
> * Развертывание приложения в IIS.

Файл параметров публикации (*\*.publishsettings*) отличается от профиля публикации (*\*.pubxml*), созданного в Visual Studio. Файл параметров публикации создается IIS или Службой приложений Azure либо может быть создан вручную, после чего его можно импортировать в Visual Studio.

> [!NOTE]
> Если вам нужно только скопировать профиль публикации Visual Studio (файл \*.pubxml) из одной установки Visual Studio в другую, можно найти профиль публикации *\<имя_профиля\>.pubxml* в папке *\\<имя_проекта\>\Properties\PublishProfiles* для управляемых типов проектов. Для веб-сайтов см. в папке *\App_Data*. Профили публикации являются XML-файлами MSBuild.

## <a name="prerequisites"></a>Предварительные требования

* У вас должна быть установлена среда Visual Studio 2017 и иметься рабочая нагрузка **ASP.NET** и **.NET Framework**. Для приложения .NET Core также требуется рабочая нагрузка **.NET Core**.

    Установите Visual Studio бесплатно со страницы  [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) , если вы еще не сделали этого.

* Чтобы создать файл параметров публикации из IIS, требуется компьютер под управлением Windows Server 2012 или Windows Server 2016, а также правильно настроенная роль веб-сервера IIS. Также требуется установить ASP.NET 4.5 и ASP.NET Core. Для ASP.NET Core см. раздел [Публикация в IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Для ASP.NET 4.5 см. раздел [IIS 8.0 — использование ASP.NET 3.5 и ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Создание проекта ASP.NET в Visual Studio

1. На компьютере, где выполняется Visual Studio, последовательно выберите **Файл** > **Создать проект**.

1. В разделе **Visual C#** или **Visual Basic** выберите **Интернет**, а затем в средней области выберите **Веб-приложение ASP.NET (.NET Framework)** или (только C#) **Веб-приложение ASP.NET Core** и нажмите кнопку **ОК**.

    Если указанные шаблоны проекта отсутствуют, выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Создать проект**. Запускается Visual Studio Installer. Ознакомьтесь с предварительными требованиями в этой статье, чтобы определить рабочие нагрузки Visual Studio, которые необходимо установить.

1. Выберите **MVC** (.NET Framework) или **Веб-приложение (модель-представление-контроллер)** (для .NET Core), убедитесь, что выбран параметр **Без проверки подлинности**, а затем нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp**, и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **Сборка** > **Собрать решение** для сборки проекта.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Установка и настройка веб-развертывания в Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Создание файла параметров публикации в IIS в Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Импорт параметров публикации в Visual Studio и развертывание

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

После успешного развертывания приложение должно запускаться автоматически. Если оно не запускается из Visual Studio, запустите его в IIS. Для ASP.NET Core необходимо убедиться, что в поле "Пул приложений" для **DefaultAppPool** задано значение **Без управляемого кода**.

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы создали файл параметров публикации, импортировали его в Visual Studio и развернули приложение ASP.NET в IIS. Рекомендуем вам ознакомиться с общими сведениями о других параметрах публикации в Visual Studio.

> [!div class="nextstepaction"]
> [Первое знакомство с развертыванием](../deployment/deploying-applications-services-and-components.md)
