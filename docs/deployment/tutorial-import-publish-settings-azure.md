---
title: Публикация в Azure посредством импорта параметров публикации
description: Создание и импорт профиля публикации для развертывания приложения из Visual Studio в службе приложений Azure
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50a65d681693bd9c1421767d2cac47f65b685e6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945049"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Публикация приложения в Службу приложений Azure посредством импорта параметров публикации в Visual Studio

Вы можете использовать средство **публикации** для импорта параметров публикации, а затем развернуть приложение. В этой статье мы используем параметры публикации для Службы приложений Azure, однако аналогичные действия можно использовать, чтобы импортировать параметры публикации из [IIS](../deployment/tutorial-import-publish-settings-iis.md). В некоторых случаях использование профиля параметров публикации может оказаться быстрее, чем ручная настройка развертывания в службу для каждой установки Visual Studio.

Эти шаги применимы к приложениям ASP.NET, ASP.NET Core и .NET Core в Visual Studio. Вы также можете импортировать параметры публикации для приложений [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Создание файла параметров публикации из Службы приложений Azure.
> * Импорт файла параметров публикации в Visual Studio.
> * Развертывание приложения в Службе приложений Azure.

Файл параметров публикации ( *\*.publishsettings*) отличается от профиля публикации ( *\*.pubxml*), созданного в Visual Studio. Файл параметров публикации создается Службой приложений Azure, после чего его можно импортировать в Visual Studio.

> [!NOTE]
> Если вам нужно только скопировать профиль публикации Visual Studio (файл *\*.pubxml*) из одной установки Visual Studio в другую, можно найти профиль публикации *\<profilename\>.pubxml* в папке *\\<имя_проекта\>\Properties\PublishProfiles* для управляемых типов проектов. Для веб-сайтов см. в папке *\App_Data*. Профили публикации являются XML-файлами MSBuild.

## <a name="prerequisites"></a>Предварительные требования

::: moniker range=">=vs-2019"

* У вас должны быть установлены решение Visual Studio 2019 и рабочая нагрузка **ASP.NET и разработка веб-приложений**.

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/), если еще не сделали этого.
::: moniker-end

::: moniker range="vs-2017"

* У вас должна быть установлена среда Visual Studio 2017 и рабочая нагрузка **ASP.NET и разработка веб-приложений**.

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/), если еще не сделали этого.
::: moniker-end

* Создайте Службу приложений Azure. Подробные инструкции см. в разделе [Развертывание веб-приложения ASP.NET Core в Azure с помощью Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Создание проекта ASP.NET в Visual Studio

1. На компьютере, где выполняется Visual Studio, создайте новый проект.

    Выберите подходящий шаблон. В данном примере выберите **Веб-приложение ASP.NET(.NET Framework)** или (только для C#) **Веб-приложение ASP.NET Core**, а затем нажмите кнопку **ОК**.

    Если вы не видите указанные шаблоны проекта, нажмите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Создание проекта**. Запускается Visual Studio Installer. Установите рабочую нагрузку **ASP.NET и веб-разработка**.

    Выбранный шаблон проекта (ASP.NET или ASP.NET Core) должен соответствовать версии ASP.NET, установленной на веб-сервере.

1. Выберите **MVC** (.NET Framework) или **Веб-приложение (модель-представление-контроллер)** (для .NET Core) и убедитесь, что выбран параметр **Без проверки подлинности**, а затем нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp**, и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **Сборка** > **Собрать решение** для сборки проекта.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Создание файла параметров публикации в Службе приложений Azure

1. Откройте Службу приложений Azure на портале Azure.

1. Перейдите в раздел **Скачать профиль публикации** и сохраните профиль локально.

    ![Скачать профиль публикации](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Файл с расширением *PUBLISHSETTINGS* был создан в расположении, куда вы его сохранили. В следующем коде показан частичный пример файла (в более удобном для чтения формате).

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

    Обычно предыдущий файл PUBLISHSETTINGS содержит два профиля публикации, которые можно использовать в Visual Studio — один для развертывания с помощью веб-развертывания, а другой для развертывания с помощью протокола FTP. Предыдущий код показывает профиль веб-развертывания. Оба профиля будут импортированы позже при импорте профиля.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Импорт параметров публикации в Visual Studio и развертывание

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы создали файл параметров публикации, импортировали его в Visual Studio и развернули приложение ASP.NET в Службе приложений Azure. Рекомендуем вам ознакомиться с общими сведениями о параметрах публикации в Visual Studio.

> [!div class="nextstepaction"]
> [Первое знакомство с развертыванием](../deployment/deploying-applications-services-and-components.md)
