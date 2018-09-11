---
title: Обзор возможностей развертывания
description: Узнайте о возможностях для развертывания приложений из Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83b6449d3f9fb41280d9e0b051c5baf3edbf5a66
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320557"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Краткое руководство: Общие сведения о развертывании в Visual Studio

Развертывание приложения, службы или компонента, его распространения для установки на других компьютерах, устройствах или серверов или в облаке. В Visual Studio можно выбрать соответствующий подход в зависимости от требуемого типа развертывания. (Множество типов приложений поддерживают другие средства развертывания, например развертывание из командной строки или NuGet, которые здесь не описываются.)

См. в разделе, краткие руководства и учебники поэтапные указания по развертыванию. Общие сведения о вариантах развертывания, см. в разделе [какие варианты публикации мне подойдут?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Развертывание в локальную папку

Развертывание в локальную папку обычно используется для тестирования или для начала промежуточное развертывание, в котором используется другое средство для окончательного развертывания.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, и. **NET Core**: использование средства публикации для развертывания в локальную папку. Доступные параметры зависят от типа приложения. В обозревателе решений щелкните правой кнопкой мыши проект и выберите **публикации**. (Если ранее вы настроили все профили публикации, нажмите кнопку **создать новый профиль**.) Затем выберите **папку**. Дополнительные сведения см. в разделе [развертывание в локальную папку](quickstart-deploy-to-local-folder.md).

    ![Выбор публикации](../deployment/media/quickstart-publish.png)

- **Среда выполнения Visual C++**: можно развернуть с помощью локальное развертывание или статическое связывание среда выполнения Visual C++. Дополнительные сведения см. в разделе [развертывание собственного приложения для настольных компьютеров (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

## <a name="publish-to-azure"></a>Публикация в Azure

- **ASP.NET**, **ASP.NET Core**, **Python**, и **Node.js**: средства публикации можно использовать для быстрого развертывания приложений в службе приложений Azure или к виртуальному Azure Компьютер. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**. (Если ранее вы настроили все профили публикации, нажмите кнопку **создать новый профиль**.) В диалоговом окне публикации выберите **службы приложений** или **виртуальных машинах**, а затем выполните действия по настройке.

    ![Выберите службу приложений Azure](../deployment/media/quickstart-publish-azure.png "выберите службу приложений Azure")

    В Visual Studio 2017 версии 15.7 и более поздние версии, вы можете развертывать приложения ASP.NET Core для **службы приложений для Linux**.

    Для приложений Python, также см. в разделе [Python — публикация в службе приложений Azure](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

    Краткое введение см. в разделе [публикация в Azure](quickstart-deploy-to-azure.md) и [опубликовать в Linux](quickstart-deploy-to-linux.md). Кроме того, см. в разделе [публикации приложения ASP.NET Core в Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Развертывание с использованием Git, см. в разделе [непрерывное развертывание ASP.NET Core в Azure с помощью Git](/aspnet/core/publishing/azure-continuous-deployment).

    Сведения о Импорт профиля публикации из службы приложений Azure в Visual Studio, см. в разделе [Импорт параметров публикации и развертывание в Azure](../deployment/tutorial-import-publish-settings-azure.md).

    > [!NOTE]
    > Если у вас еще нет учетной записи Azure, вы можете [Зарегистрируйтесь здесь](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Публикация в Интернете или развернуть в сетевую папку

- **ASP.NET**, **ASP.NET Core**, **Node.js**, и **Python**: можно использовать средства публикации для развертывания на веб-сайт, с помощью FTP или Web Deploy. Дополнительные сведения см. в разделе [развертывание на веб-сайте](quickstart-deploy-to-a-web-site.md).

    В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**. (Если ранее вы настроили все профили публикации, нажмите кнопку **создать новый профиль**.) В средства публикации выберите параметр и следуйте действия по настройке.

    ![Выберите IIS, FTP и т. д.](../deployment/media/quickstart-publish-iis-ftp.png)

    Сведения об импорте профиль публикации в Visual Studio, см. в разделе [Импорт параметров публикации и развертывания в IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Можно также развернуть приложения ASP.NET и службы в ряд других способов. Дополнительные сведения см. в разделе [развертывание ASP.NET веб-приложений и служб](http://www.asp.net/aspnet/overview/deployment).

- **Среда выполнения Visual C++**: можно развернуть среды выполнения Visual C++, с помощью центра развертывания. Дополнительные сведения см. в разделе [развертывание собственного приложения для настольных компьютеров (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

- **Windows desktop** публикацией классического приложения Windows для веб-сервера или общей сетевой папки, используя технологию ClickOnce. Затем пользователи смогут устанавливать приложение одним щелчком. Дополнительные сведения см. в разделе [развертывание классического приложения с помощью ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) и [развертывание собственного приложения с помощью ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="publish-to-microsoft-store"></a>Публикация в Microsoft Store

Из Visual Studio можно создать пакеты приложения для развертывания в Microsoft Store.

- **UWP**: можно упаковать его и развернуть его с помощью пунктов меню. Дополнительные сведения см. в разделе [упаковка приложения UWP с помощью Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Создание пакета приложения](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows desktop**: можно развернуть Microsoft Store, с помощью Desktop Bridge начиная с Visual Studio 2017 версии 15.4. Чтобы сделать это, начните с создания проект упаковки приложений Windows. Дополнительные сведения см. в разделе [упаковка классического приложения для Microsoft Store (мост для классических приложений)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Мост рабочего стола](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Развертывание на устройстве (UWP)

При развертывании приложения универсальной платформы Windows для тестирования на устройстве, см. в разделе [запуску приложений UWP на удаленном компьютере в Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-client"></a>Создание пакета установщика (клиент Windows)

Если требуется более сложную установку настольного приложения в чем [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) предоставляет, можно создать пакет установщика, проект установки или пользовательского загрузчика.

- Установщик MSI-файл WiX можно создать с помощью [WiX набора инструментов Visual Studio 2017 расширение](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) из Flexera Software можно использовать с Visual Studio 2017 (Community Edition не поддерживается). Обратите внимание, что InstallShield Limited Edition больше не входит в состав Visual Studio и не поддерживается в Visual Studio 2017: Уточните [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) о будущей доступности.

- Если вы хотите создать проект установки (vdproj), установите [расширения проектов установщика Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Путем настройки универсального установщика, который известен как начальный загрузчик, можно установить необходимые компоненты для настольных приложений. Дополнительные сведения см. в разделе [предварительные условия для развертывания приложения](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Развертывание в тестовой лаборатории

Вы можете включить более сложную разработку и тестирование, развертывание приложений в виртуальных средах. Дополнительные сведения см. в разделе [тестирования в лабораторной среде](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Развертывание DevOps

В среде группы можно использовать конвейеры Azure включить непрерывное развертывание приложения. Дополнительные сведения см. в разделе [конвейеры Azure](/azure/devops/pipelines/index?view=vsts) и [развертывание в Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deployment-for-other-app-types"></a>Развертывания для других типов приложений

| Тип приложения | Сценарий развертывания | Ссылка |
| --- | --- | --- |
| **Приложения Office** | Вы можете опубликовать надстройку для Office в Visual Studio. | [Развертывание и публикация надстройки Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Службы WCF или OData**  | Другие приложения могут использовать службы WCF RIA, развертываемые на веб-сервере. | [Разработка и развертывание служб WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch больше не поддерживается в Visual Studio 2017, но по-прежнему могут развертываться из Visual Studio 2015 и более ранних версий. | [Развертывание приложений LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы выполнили кратко рассмотрим варианты развертывания для разных приложений.

> [!div class="nextstepaction"]
> [Какие варианты публикации из них подходят для меня?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
