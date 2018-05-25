---
title: Публикация в IIS путем импорта параметров публикации
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to IIS
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 907fecd348dba46f6d3375d2d994b04ec1cf1eb5
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2018
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Публикация приложения в IIS путем импорта параметров публикации в Visual Studio

Можно использовать **публикации** , которая позволяет импортировать параметры публикации, а затем развернуть приложение. В этой статье мы используем параметры публикации для IIS, но можно использовать аналогичные действия, чтобы импортировать параметры публикации для [службе приложений Azure](../deployment/tutorial-import-publish-settings-azure.md). В некоторых случаях использование публикации, параметры профиля можно быстрее, чем Ручная настройка развертывания в службах IIS для каждой установки Visual Studio.

Эти шаги применимы к приложениям ASP.NET, .NET Core и ASP.NET Core в Visual Studio. Шаги соответствуют версии 15,6 2017 г. Visual Studio.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Настроить службы IIS, чтобы можно было создать файл параметров публикации
> * Создайте файл параметров публикации
> * Импортировать файл параметров публикации в Visual Studio
> * Развертывание приложения в IIS

Файл параметров публикации (*\*.publishsettings*) отличается от профиля публикации (*\*.pubxml*), созданных в Visual Studio. Файл параметров публикации создается в службах IIS или службе приложений Azure, или его можно создать вручную и затем его можно импортировать в Visual Studio.

> [!NOTE]
> Если требуется скопировать Visual Studio профиль публикации (\*pubxml-файл) с одной установки Visual Studio на другую, можно найти профиль публикации,  *\<profilename\>.pubxml*, в  *\\< имя_проекта\>\Properties\PublishProfiles* папку для типов управляемых проектов. Веб-сайтов, см. в разделе *\App_Data* папки. Профили публикации являются файлами MSBuild XML.

## <a name="prerequisites"></a>Предварительные требования

* Необходимо иметь Visual Studio 2017 г. установлен и **ASP.NET** и **.NET Framework** разработки рабочей нагрузки. Для приложения .NET Core, необходимо также **.NET Core** рабочей нагрузки.

    Установите Visual Studio бесплатно [здесь](http://www.visualstudio.com), если еще не сделали это.

* Чтобы создать файл параметров публикации на основе IIS, необходимо иметь компьютер под управлением Windows Server 2012 или Windows Server 2016 и необходимо иметь роль веб-сервера IIS правильно настроена. Также можно установить ASP.NET 4.5 или ASP.NET Core. ASP.NET Core. в разделе [публикация в службах IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET 4.5 см. в разделе [IIS 8.0 с помощью ASP.NET 3.5 и ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Создайте новый проект ASP.NET в Visual Studio

1. На компьютере под управлением Visual Studio, выберите **файл > Новый проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **Web**, а затем в средней области выберите **веб-приложения ASP.NET (.NET Framework)**(только C#) или **веб-приложения ASP.NET Core**, а затем нажмите кнопку **ОК**.

    Если вы не видите шаблоны указанный проект, нажмите кнопку **откройте установщик Visual Studio** ссылку в левой области **новый проект** диалоговое окно. Запускается Visual Studio Installer. См. в этой статье, чтобы определить необходимые рабочие нагрузки Visual Studio, которые необходимо установить необходимые компоненты.

1. Выберите либо **MVC** (.NET Framework) или **веб-приложения (Model-View-Controller)** (для .NET Core) и убедитесь, что **без проверки подлинности** выбран и нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **сборки > построить решение** для сборки проекта.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Установка и настройка веб-развертывания на Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Создать файл параметров публикации в службах IIS в Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Импорт параметров публикации в Visual Studio и развертывание

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

После успешного развертывает приложение, должен запускаться автоматически. Если она не запускается из Visual Studio, запустите приложение в службах IIS. Для ASP.NET Core необходимо убедитесь в том, что пул приложений поля для **DefaultAppPool** равно **без управляемого кода**.

## <a name="next-steps"></a>Следующие шаги

В этом учебнике создан файл параметров публикации, импортировать его в Visual Studio и развертывания приложения ASP.NET в IIS.

> [!div class="nextstepaction"]
> [Первое знакомство с развертыванием](../deployment/deploying-applications-services-and-components.md)
