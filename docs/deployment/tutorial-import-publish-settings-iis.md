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
ms.openlocfilehash: e6df935578955d3c72b6f4fa61efdf614229bca0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808469"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Публикация приложения в службах IIS путем импорта параметров публикации в Visual Studio

Можно использовать **публикации** средство для импорта параметров публикации, а затем развернуть приложение. В этой статье мы используем параметры публикации для IIS, но можно использовать аналогичные действия, чтобы импортировать параметры публикации для [службе приложений Azure](../deployment/tutorial-import-publish-settings-azure.md). В некоторых случаях использование публикации, параметры профиля можно быстрее, чем Ручная настройка развертывания в IIS, для каждой установки Visual Studio.

Эти шаги применимы к приложениям ASP.NET, ASP.NET Core и .NET Core в Visual Studio. Шаги соответствуют Visual Studio 2017 версии 15.6.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Настроить службы IIS таким образом, можно создать файл параметров публикации
> * Создайте файл параметров публикации
> * Импортировать файл параметров публикации в Visual Studio
> * Развертывание приложения в IIS

Файл параметров публикации (*\*.publishsettings*) отличается от профиля публикации (*\*.pubxml*), созданных в Visual Studio. В службах IIS или службе приложений Azure, создается файл параметров публикации или его можно создать вручную, и его можно было импортировать в Visual Studio.

> [!NOTE]
> Если вам нужно только скопировать Visual Studio, профиль публикации (\*pubxml-файл) с одной установки Visual Studio в другую, можно найти профиль публикации,  *\<profilename\>.pubxml*, в  *\\< имя_проекта\>\Properties\PublishProfiles* папку для типов управляемых проектов. Веб-сайтов, см. в разделе *\App_Data* папки. Профили публикации являются файлами MSBuild XML.

## <a name="prerequisites"></a>Предварительные требования

* Необходимо установить Visual Studio 2017 и **ASP.NET** и **.NET Framework** рабочая нагрузка разработки. Для приложения .NET Core, необходимо также **.NET Core** рабочей нагрузки.

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

* Чтобы создать файл параметров публикации на основе IIS, необходимо иметь компьютер под управлением Windows Server 2012 или Windows Server 2016, и необходимо иметь роль веб-сервера IIS, которые правильно настроены. Также можно установить ASP.NET 4.5 и ASP.NET Core. ASP.NET Core, см. в разделе [публикация в службах IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET 4.5 см. в разделе [IIS 8.0 с ASP.NET 3.5 и ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Создайте новый проект ASP.NET в Visual Studio

1. На компьютере с Visual Studio, выберите **файл** > **новый проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **Web**, а затем в средней области выберите либо **веб-приложение ASP.NET (.NET Framework)**(только C#) или **веб-приложение ASP.NET Core**, а затем нажмите кнопку **ОК**.

    Если вы не видите шаблоны указанный проект, нажмите кнопку **открыть установщик Visual Studio** ссылку в левой части **новый проект** диалоговое окно. Запускается Visual Studio Installer. Предварительные требования в этой статье, чтобы определить необходимые рабочие нагрузки Visual Studio, которые необходимо установить.

1. Выберите либо **MVC** (.NET Framework) или **веб-приложение (Model-View-Controller)** (для .NET Core) и убедитесь, что **без проверки подлинности** выбран, а затем нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **построения** > **построить решение** для сборки проекта.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Установка и настройка веб-развертывания в Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Создайте файл параметров публикации в службах IIS на Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Импорт параметров публикации в Visual Studio и развертывание

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

После успешного развертывания приложения должен запускаться автоматически. Если он не запускается из Visual Studio, запустите приложение в IIS. Для ASP.NET Core, необходимо убедиться, что пул приложений поле для **DefaultAppPool** присваивается **без управляемого кода**.

## <a name="next-steps"></a>Следующие шаги

В этом руководстве создан файл параметров публикации, импортировать его в Visual Studio и развертывания приложения ASP.NET в IIS. Вы можете Общие сведения о других параметрах публикации в Visual Studio.

> [!div class="nextstepaction"]
> [Первое знакомство с развертыванием](../deployment/deploying-applications-services-and-components.md)
