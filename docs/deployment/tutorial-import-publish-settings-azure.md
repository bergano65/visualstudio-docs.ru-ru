---
title: Опубликовать в Azure путем импорта параметров публикации
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 88dc37e555f6ceb30584d4a1c17b96506219631a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766744"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Публикация приложения в службе приложений Azure путем импорта параметров публикации в Visual Studio

Можно использовать **публикации** , которая позволяет импортировать параметры публикации, а затем развернуть приложение. В этой статье мы используем параметры публикации для службы приложений Azure, но можно использовать аналогичные действия, чтобы импортировать параметры из публикации [IIS](../deployment/tutorial-import-publish-settings-iis.md). В некоторых случаях использование публикации, параметры профиля можно быстрее, чем Ручная настройка развертывания службы для каждой установки Visual Studio.

Эти шаги применимы к приложениям ASP.NET, .NET Core и ASP.NET Core в Visual Studio. Вы также можете импортировать параметры публикации для [Python](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio) приложений. Шаги соответствуют версии 15,6 2017 г. Visual Studio.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Создать файл параметров публикации из службы приложений Azure
> * Импортировать файл параметров публикации в Visual Studio
> * Развертывание приложения в службе приложений Azure

Файл параметров публикации (*\*.publishsettings*) отличается от профиля публикации (*\*.pubxml*), созданных в Visual Studio. Файл параметров публикации создается службой приложений Azure, и его можно было импортировать в Visual Studio.

> [!NOTE]
> Если требуется скопировать Visual Studio профиль публикации (*\*.pubxml* файл) с одной установки Visual Studio на другую, можно найти профиль публикации,  *\<profilename\>.pubxml*в  *\\< имя_проекта\>\Properties\PublishProfiles* папку для типов управляемых проектов. Веб-сайтов, см. в разделе *\App_Data* папки. Профили публикации являются файлами MSBuild XML.

## <a name="prerequisites"></a>Предварительные требования

* Необходимо иметь Visual Studio 2017 г. установлен и **ASP.NET** и. **NET Framework** разработки рабочей нагрузки. Для приложения .NET Core, необходимо также. **NET Core** рабочей нагрузки.

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

* Создайте службу приложений Azure. Подробные инструкции см. в разделе [развернуть веб-приложение ASP.NET Core в Azure, с помощью Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Создайте новый проект ASP.NET в Visual Studio

1. На компьютере под управлением Visual Studio, выберите **файл > Новый проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **Web**, а затем в средней области выберите **веб-приложения ASP.NET (.NET Framework)**(только C#) или **веб-приложения ASP.NET Core**, а затем нажмите кнопку **ОК**.

    Если вы не видите шаблоны указанный проект, нажмите кнопку **откройте установщик Visual Studio** ссылку в левой области **новый проект** диалоговое окно. Запускается Visual Studio Installer. См. в этой статье, чтобы определить необходимые рабочие нагрузки Visual Studio, которые необходимо установить необходимые компоненты.

1. Выберите либо **MVC** (.NET Framework) или **веб-приложения (Model-View-Controller)** (для .NET Core) и убедитесь, что **без проверки подлинности** выбран и нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **сборки > построить решение** для сборки проекта.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Создайте файл параметров публикации в службе приложений Azure

1. На портале Azure откройте службы приложений Azure.

1. Нажмите кнопку **получение профиля публикации** и сохраните профиль локально.

    ![Получение профиля публикации](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Файл с *.publishsettings* расширение файла был создан в расположение, где был сохранен. Ниже показан пример частичного файла (в более удобном для чтения форматирования).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    Как правило выше *.publishsettings файл содержит два профили публикации, которые можно использовать в Visual Studio для развертывания с помощью веб-развертывания и один для развертывания с помощью протокола FTP. Предыдущий код показывает профиль веб-развертывания. Оба профиля будут импортированы позже при импорте профиля.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Импорт параметров публикации в Visual Studio и развертывание

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Следующие шаги

В этом учебнике создан файл параметров публикации, импортировать его в Visual Studio и развертывания приложения ASP.NET в службе приложений Azure. Вы можете Обзор публикации параметров в Visual Studio.

> [!div class="nextstepaction"]
> [Первое знакомство с развертыванием](../deployment/deploying-applications-services-and-components.md)
