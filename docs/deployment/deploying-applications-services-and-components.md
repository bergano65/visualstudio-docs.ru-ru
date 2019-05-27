---
title: Обзор возможностей развертывания
description: Сведения о вариантах развертывания приложений из среды Visual Studio.
ms.custom: mvc
ms.date: 01/29/2019
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e66eb7fc2915514b91135e8c89843a0d979abf4a
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65845910"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Знакомство с возможностями развертывания в Visual Studio

Развертывание приложения, службы или компонента — это механизм их распространения для установки на других компьютерах, устройствах, серверах и в облаке. В Visual Studio можно выбрать соответствующий подход в зависимости от требуемого типа развертывания. (Многие приложения различных типов поддерживают другие средства развертывания, такие как развертывание из командной строки или NuGet, которые не описываются в этой статье.)

Пошаговые инструкции по развертыванию см. в кратких руководствах и учебниках. Обзор вариантов развертывания см. в статье [Выбор подходящих вариантов публикации](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Развертывание в локальную папку

Развертывание в локальную папку, как правило, осуществляется для тестирования или на начальном этапе промежуточного развертывания, после которого для окончательного развертывания будет использовано другое средство.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** и **.NET Core**. Для развертывания в локальную папку используйте средство публикации. Выбор варианта зависит типа приложения. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**. (Если профили публикации не были настроены ранее, необходимо щелкнуть **Создать профиль**.) Далее выберите **Папка**. Дополнительные сведения см. в статье [Развертывание в локальную папку](quickstart-deploy-to-local-folder.md).

    ![Выбор команды "Опубликовать"](../deployment/media/quickstart-publish.png)

- **Классические приложения Windows**. Вы можете публиковать классические приложения Windows в папке, используя развертывание ClickOnce. Затем пользователи смогут устанавливать приложение одним щелчком. Дополнительные сведения см. в статье [Развертывание классического приложения с помощью ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# и Visual Basic). Для C + +/ CLR см. раздел [Развертывание собственного приложения с помощью ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications). Для C/C++ см. раздел [Развертывание собственного приложения с помощью проекта установки](/cpp/ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Публикация в Azure

- **ASP.NET**, **ASP.NET Core**, **Python** и **Node.js**. Публикуйте приложения в службе приложений Azure или службе приложений Azure в Linux (с помощью контейнеров), используя один из следующих методов.

  - Для непрерывного (или автоматического) развертывания приложений используйте Azure DevOps с [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops).

  - Для однократного развертывания приложений (или развертывания вручную) используйте средство **публикации** в Visual Studio.

  Чтобы иметь больше возможностей для настройки конфигурации сервера, также можно использовать средство **публикации** для развертывания приложений на виртуальной машине Azure.

  Чтобы использовать средство **публикации**, щелкните правой кнопкой мыши проект в обозревателе решений и выберите **Опубликовать**. (Если ранее вы настроили профили публикации, затем необходимо выбрать команду **Создать новый профиль**.) В диалоговом окне публикации выберите **Служба приложений** или **Виртуальная машина Azure** и выполните инструкции по настройке.

  ![Выбор службы приложений Azure](../deployment/media/quickstart-publish-azure.png "Выбор службы приложений Azure")

  Начиная с Visual Studio 2017 версии 15.7 приложения ASP.NET Core можно развертывать в **Службе приложений для Linux**.

  Информацию о приложениях Python см. в статье [Python. Публикация в службу приложений Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Краткое ознакомительное руководство приводится в статьях [Публикация в Azure](quickstart-deploy-to-azure.md) и [Публикация в Linux](quickstart-deploy-to-linux.md). Также см. статью [Публикация приложения ASP.NET Core в Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Информацию о развертывании с использованием Git см. в статье [Непрерывное развертывание ASP.NET Core в Azure с помощью Git](/aspnet/core/publishing/azure-continuous-deployment).

  Дополнительные сведения об импорте профиля публикации из службы приложений Azure в Visual Studio см. в статье [Импорт параметров публикации и развертывание в Azure](../deployment/tutorial-import-publish-settings-azure.md).

  > [!NOTE]
  > Если у вас нет учетной записи Azure, вы можете [зарегистрироваться здесь](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Публикация в Интернете или развертывание в сетевую папку

- **ASP.NET**, **ASP.NET Core**, **Node.js** и **Python**. С помощью средства публикации вы можете развернуть веб-сайт, используя FTP или веб-развертывание. Дополнительные сведения см. в статье [Развертывание на веб-сайт](quickstart-deploy-to-a-web-site.md).

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**. (Если ранее вы настроили профили публикации, затем необходимо выбрать команду **Создать новый профиль**.) В средстве "Опубликовать" выберите нужный вариант и выполните инструкции по установке.

    ![Выберите IIS, FTP или другой вариант.](../deployment/media/quickstart-publish-iis-ftp.png)

    Дополнительные сведения об импорте профиля публикации в Visual Studio см. в статье [Импорт параметров публикации и развертывание в IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Также вы можете развертывать приложения и службы ASP.NET некоторыми другими способами. Дополнительные сведения см. в статье [Развертывание веб-приложений и служб ASP.NET](http://www.asp.net/aspnet/overview/deployment).

- **Классические приложения Windows**. Вы можете публиковать классические приложения Windows на веб-сервере или в общей сетевой папке, используя развертывание ClickOnce. Затем пользователи смогут устанавливать приложение одним щелчком. Дополнительные сведения см. в статье [Развертывание классического приложения с помощью ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# и Visual Basic). Для C + +/ CLR см. раздел [Развертывание собственного приложения с помощью ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications). Для C/C++ см. раздел [Развертывание собственного приложения с помощью проекта установки](/cpp/ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-microsoft-store"></a>Публикация в Microsoft Store

В среде Visual Studio можно создавать пакеты приложений для развертывания в Microsoft Store.

- **Универсальная платформа Windows**. Вы можете упаковать свое приложение и развернуть его, используя пункты меню. Дополнительные сведения см. в статье [Упаковка приложения UWP с помощью Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Создание пакета приложения](../deployment/media/feature-tour-create-app-package.jpg)

- **Классические приложения Windows**. Начиная с версии Visual Studio 2017 15.4, вы можете выполнять развертывание в Microsoft Store, используя мост для классических приложений. Для этого сначала необходимо создать проект упаковки приложений Windows. Дополнительные сведения см. в статье [Упаковка классического приложения для Microsoft Store (мост для классических приложений)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Мост для классических приложений](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Развертывание на устройство (универсальная платформа Windows)

Если вы развертываете приложение универсальной платформы Windows на устройство в целях тестирования, ознакомьтесь со статьей [Запуск приложений UWP на удаленном компьютере в среде Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Создание пакета установщика (классическое приложение Windows)

Если возможностей [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) недостаточно для установки вашего классического приложения, вы можете создать пакет установщика Windows (файл установки MSI или EXE) или собственный начальный загрузчик.

- Пакет установщика на базе MSI можно создать с помощью [расширения с набором инструментов WiX для Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). Это программа командной строки.

- Пакет установщика MSI или EXE можно создать, используя [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) из Flexera Software. Вместе с Visual Studio 2017 и последующими версиями можно использовать компонент InstallShield (выпуск Community Edition не поддерживается). Обратите внимание, что версия InstallShield Limited Edition больше не входит в состав среды Visual Studio и не поддерживается в Visual Studio 2017 и последующих версиях. Информацию о ее дальнейшей доступности см. в документации по [программному обеспечению Flexera](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio).

- Пакет установщика MSI или EXE можно создать с помощью проекта установки (VDPROJ). Чтобы использовать этот вариант, установите [расширение проектов Visual Studio Installer](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Вы также можете установить компоненты, необходимые для классических приложений, путем настройки универсального установщика, также называемого начальным загрузчиком. Дополнительные сведения см. в статье [Предварительные условия для развертывания приложения](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Развертывание в тестовой лаборатории

Чтобы иметь возможности для реализации более сложных сценариев разработки и тестирования, можно развертывать приложения в виртуальных средах. Дополнительные сведения см. в статье [Тестирование в лабораторной среде](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Непрерывное развертывание

Для непрерывного развертывания приложения можно использовать Azure Pipelines. Дополнительные сведения см. в статьях [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) и [Развертывание в Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deployment-for-other-app-types"></a>Развертывания приложений других типов

| Тип приложения | Сценарий развертывания | Ссылка |
| --- | --- | --- |
| **Приложения Office** | Из среды Visual Studio можно опубликовать надстройку для Office. | [Развертывание и публикация надстройки Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Службы WCF или OData** | Другие приложения могут использовать службы RIA WCF, развертываемые на веб-сервере. | [Разработка и развертывание служб WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | Начиная с Visual Studio 2017, среда LightSwitch более не поддерживается, но можно выполнить ее развертывание в Visual Studio 2015 и предыдущих версиях. | [Развертывание приложений LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Следующие шаги

В этом руководстве кратко рассматриваются возможные варианты развертывания различных приложений.

> [!div class="nextstepaction"]
> [Выбор подходящих вариантов публикации](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
