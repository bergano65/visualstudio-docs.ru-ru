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
ms.openlocfilehash: a0fcc9f6ec4143a757139a9e013f1a1f4dbe666e
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Публикация приложения в службе приложений Azure путем импорта параметров публикации в Visual Studio

Можно использовать **публикации** , которая позволяет импортировать параметры публикации, а затем развернуть приложение. В этой статье мы используем параметры публикации для службы приложений Azure, но можно использовать аналогичные действия, чтобы импортировать параметры из публикации [IIS](../deployment/tutorial-import-publish-settings-iis.md). В некоторых случаях использование публикации, параметры профиля можно быстрее, чем Ручная настройка развертывания службы для каждой установки Visual Studio.

Эти шаги применимы к приложениям ASP.NET, .NET Core и ASP.NET Core в Visual Studio. Шаги соответствуют версии 15,6 2017 г. Visual Studio.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Создать файл параметров публикации из службы приложений Azure
> * Импортировать файл параметров публикации в Visual Studio
> * Развертывание приложения в службе приложений Azure

Файл параметров публикации (*.publishsettings) отличается от профиля публикации (*.pubxml), созданных в Visual Studio. Файл параметров публикации создается службой приложений Azure, и его можно было импортировать в Visual Studio.

> [!NOTE]
> Если требуется скопировать Visual Studio профиль публикации (\*pubxml-файл) с одной установки Visual Studio на другую, можно найти профиль публикации,  *\<profilename\>.pubxml*, в  *\\< имя_проекта\>\Properties\PublishProfiles* папку для типов управляемых проектов. Веб-сайтов, см. в разделе *\App_Data* папки. Профили публикации являются файлами MSBuild XML.

## <a name="prerequisites"></a>Предварительные требования

* Необходимо иметь установленной среды Visual Studio и **ASP.NET** и **.NET Framework** разработки рабочей нагрузки. Для приложения .NET Core, необходимо также **.NET Core** рабочей нагрузки.

    Установите Visual Studio бесплатно [здесь](http://www.visualstudio.com), если еще не сделали это.

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

1. На компьютере, где имеется проект ASP.NET, откройте в Visual Studio, щелкните правой кнопкой мыши проект в обозревателе решений и выберите **публикации**.

1. Если были настроены ранее все профили публикации **публикации** появится область. Нажмите кнопку **Создание нового профиля**.

1. В **выбрать место назначения публикации** диалоговое окно, нажмите кнопку **Импорт профиля**.

    ![Выберите опубликовать](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Перейдите к расположению файла параметров публикации, созданной в предыдущем разделе.

1. В **файл параметров публикации импорта** диалоговое окно, выберите профиль, созданный в предыдущем разделе и нажмите кнопку **откройте**.

1. Выберите один из двух импортированных профилей и нажмите кнопку **публикации**.

    Visual Studio запускает процесс развертывания, и в окне вывода отображаются хода выполнения и результатов.

## <a name="next-steps"></a>Следующие шаги

В этом учебнике создан файл параметров публикации, импортировать его в Visual Studio и развертывания приложения ASP.NET в службе приложений Azure.

> [!div class="nextstepaction"]
> [Первое знакомство с развертыванием](../deployment/deploying-applications-services-and-components.md)
