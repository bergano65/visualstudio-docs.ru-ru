---
title: Первое знакомство с развертыванием
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8933127940cd8155bbf0854fd19c559022bceecb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912171"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Знакомство с возможностями развертывания в Visual Studio

Развертывание приложения, службы или компонента — это механизм их распространения для установки на других компьютерах, устройствах, серверах и в облаке. В Visual Studio можно выбрать соответствующий подход в зависимости от требуемого типа развертывания. (Многие приложения различных типов поддерживают другие средства развертывания, такие как развертывание из командной строки или NuGet, которые не описываются в этой статье.)

Пошаговые инструкции по развертыванию см. в кратких руководствах и учебниках. Обзор вариантов развертывания см. в статье [Выбор подходящих вариантов публикации](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-a-local-folder"></a>Развертывание в локальную папку

Развертывание в локальную папку, как правило, осуществляется для тестирования или на начальном этапе промежуточного развертывания, после которого для окончательного развертывания будет использовано другое средство.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** и **.NET Core**. Для развертывания в локальную папку используйте средство **публикации**. Выбор варианта зависит типа приложения. В обозревателе решений щелкните проект правой кнопкой мыши и выберите **Опубликовать**. (Если профили публикации не были настроены ранее, необходимо щелкнуть **Создать профиль**.) Выберите элемент **Папка**. Дополнительные сведения см. в статье [Развертывание в локальную папку](quickstart-deploy-to-local-folder.md).

    ![Снимок экрана: выбор пункта "Опубликовать".](../deployment/media/quickstart-publish.png)

- **Классические приложения Windows**. Вы можете публиковать классические приложения Windows в папке, используя развертывание ClickOnce. Затем пользователи смогут устанавливать приложение одним щелчком. Дополнительные сведения см. в следующих статьях:

  - [Развертывание классического приложения Windows .NET Framework с помощью ClickOnce.](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [Развертывание классического приложения Windows .NET с помощью ClickOnce.](quickstart-deploy-using-clickonce-folder.md)
  - См. статью [Развертывание приложения C++/CLR с помощью ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications). Для C/C++ см. статью [Развертывание нативного приложения с помощью проекта установки](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Публикация в Azure

- **ASP.NET**, **ASP.NET Core**, **Python** и **Node.js**. Публикуйте приложения в Службе приложений Azure или Службе приложений Azure в Linux (с помощью контейнеров), используя один из следующих методов:

  - Для непрерывного (или автоматического) развертывания приложений используйте Azure DevOps с [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).
  - Для однократного развертывания приложений (или развертывания вручную) используйте средство **публикации** в Visual Studio.

  Чтобы иметь больше возможностей для настройки конфигурации сервера, также можно использовать средство **публикации** для развертывания приложений на виртуальной машине Azure.

  Чтобы использовать средство **публикации**, щелкните правой кнопкой мыши проект в обозревателе решений и выберите **Опубликовать**. (Если профили публикации не были настроены ранее, необходимо щелкнуть **Создать профиль**.) В диалоговом окне **Публикация** выберите **Служба приложений** или **Виртуальные машины Azure** и выполните инструкции по настройке.

  ![Снимок экрана: выбор Службы приложений Azure.](../deployment/media/quickstart-publish-azure-new.png "Выбор службы приложений Azure")

  Начиная с Visual Studio 2017 версии 15.7 приложения ASP.NET Core можно развертывать в Службе приложений для Linux.

  Информацию о приложениях Python см. в статье [Python. Публикация в службу приложений Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Краткое ознакомительное руководство приводится в статьях [Публикация в Azure](quickstart-deploy-to-azure.md) и [Публикация в Linux](quickstart-deploy-to-linux.md). Также см. статью [Публикация приложения ASP.NET Core в Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Информацию о развертывании с использованием Git см. в статье [Непрерывное развертывание ASP.NET Core в Azure с помощью Git](/aspnet/core/publishing/azure-continuous-deployment).

  > [!NOTE]
  > Если у вас нет учетной записи Azure, вы можете зарегистрироваться [здесь](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-the-web-or-deploy-to-a-network-share"></a>Публикация в Интернете или развертывание в сетевой папке

- **ASP.NET**, **ASP.NET Core**, **Node.js** и **Python**. С помощью средства **публикации** вы можете выполнить развертывание на веб-сайт, используя FTP или веб-развертывание. Дополнительные сведения см. в статье [Публикация веб-приложения на веб-сайте с помощью Visual Studio](quickstart-deploy-to-a-web-site.md).

    В Обозревателе решений щелкните проект правой кнопкой мыши и выберите **Опубликовать**. (Если профили публикации не были настроены ранее, необходимо щелкнуть **Создать профиль**.) В средстве **публикации** выберите нужный вариант и выполните инструкции по настройке.

    ![Снимок экрана: выбор служб IIS.](../deployment/media/quickstart-publish-iis.png)

    Дополнительные сведения об импорте профиля публикации в Visual Studio см. в статье [Импорт параметров публикации и развертывание в IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Также вы можете развертывать приложения и службы ASP.NET некоторыми другими способами. Дополнительные сведения см. в статье [Развертывание веб-приложений и служб ASP.NET](/aspnet/overview/deployment).

- **Классические приложения Windows**. Вы можете публиковать классическое приложение Windows на веб-сервере или в общей сетевой папке, используя развертывание ClickOnce. Затем пользователи смогут устанавливать приложение одним щелчком. Дополнительные сведения см. в следующих статьях:

  - [Развертывание классического приложения Windows .NET Framework с помощью ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [Развертывание классического приложения Windows .NET с помощью ClickOnce](quickstart-deploy-using-clickonce-folder.md)
  - [Развертывание приложения C++/CLR с помощью ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

## <a name="publish-to-microsoft-store"></a>Публикация в Microsoft Store

В среде Visual Studio можно создавать пакеты приложений для развертывания в Microsoft Store.

- **Универсальная платформа Windows**. Вы можете упаковать свое приложение и развернуть его, используя пункты меню. Дополнительные сведения см. в статье [Упаковка приложения UWP с помощью Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Снимок экрана: создание пакета приложения.](../deployment/media/feature-tour-create-app-package.png)

- **Классические приложения Windows**. Начиная с версии Visual Studio 2017 15.4, вы можете выполнять развертывание в Microsoft Store, используя мост для классических приложений. Для этого сначала необходимо создать проект упаковки приложений Windows. Дополнительные сведения см. в статье [Упаковка классического приложения для Microsoft Store (мост для классических приложений)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Снимок экрана: выбор Проекта упаковки приложений Windows.](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Развертывание на устройство (универсальная платформа Windows)

Если вы развертываете приложение универсальной платформы Windows на устройство в целях тестирования, ознакомьтесь со статьей [Запуск приложений UWP на удаленном компьютере в среде Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Создание пакета установщика (классическое приложение Windows)

Если возможностей ClickOnce недостаточно для установки вашего классического приложения, вы можете создать пакет установщика Windows (файл установки MSI или EXE) или собственный начальный загрузчик.

- Пакет установщика на базе MSI можно создать с помощью [расширения с набором инструментов WiX для Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). Это программа командной строки.
- Пакет установщика MSI или EXE можно создать, используя [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) от Flexera Software. Вместе с Visual Studio 2017 и последующими версиями можно использовать компонент InstallShield. Выпуск Community Edition не поддерживается.

  > [!NOTE]
  > Версия InstallShield Limited Edition больше не входит в состав Visual Studio и не поддерживается в Visual Studio 2017 и последующих версиях. Информацию о ее дальнейшей доступности см. в документации [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio).

- Пакет установщика MSI или EXE можно создать с помощью проекта установки (VDPROJ). Чтобы использовать этот вариант, установите [расширение проектов Visual Studio Installer](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).
- Вы также можете установить компоненты, необходимые для классических приложений, путем настройки универсального установщика, также называемого начальным загрузчиком. Дополнительные сведения см. в статье [Предварительные условия для развертывания приложения](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-a-test-lab"></a>Развертывание в тестовой лаборатории

Чтобы иметь возможности для реализации более сложных сценариев разработки и тестирования, можно развертывать приложения в виртуальных средах. Дополнительные сведения см. в статье [Тестирование в лабораторной среде](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Непрерывное развертывание

Для непрерывного развертывания приложения можно использовать Azure Pipelines. Дополнительные сведения см. в статьях [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) и [Развертывание в Azure](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true).

## <a name="deploy-a-sql-database"></a>Развертывание базы данных SQL

- [Изменение целевой платформы и публикация проекта базы данных (SQL Server Data Tools (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)
- [Развертывание проекта Analysis Services (SQL Server Analysis Services)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)
- [Развертывание проектов и пакетов Integration Services (MSSQL Integration Services)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)
- [Создание и развертывание в локальной базе данных](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Развертывания приложений других типов

| Тип приложения | Сценарий развертывания | Ссылка |
| --- | --- | --- |
| **Приложения Office** | Из среды Visual Studio можно опубликовать надстройку для Office. | [Развертывание и публикация надстройки Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Службы WCF или OData** | Другие приложения могут использовать службы RIA WCF, развертываемые на веб-сервере. | [Разработка и развертывание служб WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | Начиная с Visual Studio 2017, среда LightSwitch более не поддерживается, но можно выполнить ее развертывание в Visual Studio 2015 и предыдущих версиях. | [Развертывание приложений LightSwitch](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>Следующие шаги

В этом руководстве кратко рассматриваются возможные варианты развертывания различных приложений.

> [!div class="nextstepaction"]
> [Выбор подходящих вариантов публикации](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)