---
title: Публикация в Azure путем импорта параметров публикации
ms.description: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 2b4b0e4ea963f20199267f32a8c87440c8cc350b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808325"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Публикация приложения в службе приложений Azure путем импорта параметров публикации в Visual Studio

Можно использовать **публикации** средство для импорта параметров публикации, а затем развернуть приложение. В этой статье мы используем параметры публикации для службы приложений Azure, но можно использовать аналогичные действия, чтобы импортировать параметры публикации из [IIS](../deployment/tutorial-import-publish-settings-iis.md). В некоторых случаях использование публикации, параметры профиля можно быстрее, чем вручную настраивать развертывание в службе для каждой установки Visual Studio.

Эти шаги применимы к приложениям ASP.NET, ASP.NET Core и .NET Core в Visual Studio. Вы также можете импортировать параметры публикации для [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) приложений. Шаги соответствуют Visual Studio 2017 версии 15.6.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Создать файл параметров публикации в службе приложений Azure
> * Импортировать файл параметров публикации в Visual Studio
> * Развертывание приложения в службе приложений Azure

Файл параметров публикации (*\*.publishsettings*) отличается от профиля публикации (*\*.pubxml*), созданных в Visual Studio. Файл параметров публикации создается службой приложений Azure, а затем его можно импортировать в Visual Studio.

> [!NOTE]
> Если вам нужно только скопировать Visual Studio, профиль публикации (*\*.pubxml* файл) с одной установки Visual Studio в другую, можно найти профиль публикации,  *\<profilename\>.pubxml*в  *\\< имя_проекта\>\Properties\PublishProfiles* папку для типов управляемых проектов. Веб-сайтов, см. в разделе *\App_Data* папки. Профили публикации являются файлами MSBuild XML.

## <a name="prerequisites"></a>Предварительные требования

* Необходимо установить Visual Studio 2017 и **ASP.NET** и. **NET Framework** рабочая нагрузка разработки. Для приложения .NET Core, необходимо также. **NET Core** рабочей нагрузки.

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

* Создайте службу приложений Azure. Подробные инструкции см. в разделе [развернуть веб-приложение ASP.NET Core в Azure с помощью Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Создайте новый проект ASP.NET в Visual Studio

1. На компьютере с Visual Studio, выберите **файл** > **новый проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **Web**, а затем в средней области выберите либо **веб-приложение ASP.NET (.NET Framework)**(только C#) или **веб-приложение ASP.NET Core**, а затем нажмите кнопку **ОК**.

    Если вы не видите шаблоны указанный проект, нажмите кнопку **открыть установщик Visual Studio** ссылку в левой части **новый проект** диалоговое окно. Запускается Visual Studio Installer. Предварительные требования в этой статье, чтобы определить необходимые рабочие нагрузки Visual Studio, которые необходимо установить.

1. Выберите либо **MVC** (.NET Framework) или **веб-приложение (Model-View-Controller)** (для .NET Core) и убедитесь, что **без проверки подлинности** выбран, а затем нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **построения** > **построить решение** для сборки проекта.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Создание файла параметров публикации в службе приложений Azure

1. На портале Azure Откройте службу приложений Azure.

1. Нажмите кнопку **получить профиль публикации** и сохраните профиль локально.

    ![Получение профиля публикации](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Файл с *.publishsettings* расширение файла был создан в расположении, где был сохранен. В следующем коде показано частично представлен пример файла (в более удобном для чтения форматирования).

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
    Как правило предыдущий файл *.publishsettings содержит два профиля публикации, которые можно использовать в Visual Studio для развертывания с помощью веб-развертывания и один для развертывания с помощью протокола FTP. Предыдущий код показывает профиль веб-развертывания. Оба профиля импортируется позже при импорте профиля.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Импорт параметров публикации в Visual Studio и развертывание

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Следующие шаги

В этом руководстве создан файл параметров публикации, импортировать его в Visual Studio и развернули приложение ASP.NET в службе приложений Azure. Вы можете Общие сведения о параметрах публикации в Visual Studio.

> [!div class="nextstepaction"]
> [Первое знакомство с развертыванием](../deployment/deploying-applications-services-and-components.md)
