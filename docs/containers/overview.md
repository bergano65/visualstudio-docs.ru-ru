---
title: Средства Visual Studio для контейнеров в Windows
description: Изучите средства, доступные в Visual Studio для работы с Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0d5859016a02de259c24c213c6cfef8cb5fce005
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916564"
---
# <a name="container-tools-in-visual-studio"></a>Средства для контейнеров в Visual Studio

Доступные в Visual Studio средства для разработки с помощью контейнеров просты в использовании и значительно упрощают сборку, отладку и развертывание контейнерных приложений. Можно работать над одним проектом с использованием контейнера или применять оркестрацию контейнеров с Service Fabric, Docker Compose либо Kubernetes для работы с несколькими службами в контейнерах.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Предварительные требования

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) с рабочей нагрузкой **Веб-разработка**, **Средства Azure** и (или) **Кроссплатформенная разработка .NET Core**
* Для публикации в Реестр контейнеров Azure требуется подписка Azure. [Зарегистрируйтесь для получения бесплатной пробной версии](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Поддержка Docker в Visual Studio

Поддержка Docker доступна в проектах ASP.NET, ASP.NET Core и консольных проектах .NET Core и .NET Framework.

Поддержка Docker в Visual Studio оптимизировалась с каждым выпуском программы с учетом пожеланий пользователей. Есть два уровня поддержки Docker, которые можно добавить в проект. Набор поддерживаемых возможностей зависит от типа проекта и версии Visual Studio. Если вам необходим контейнер для работы над отдельным проектом, а не оркестрация, для некоторых типов проектов можно просто добавить поддержку Docker.  Следующий уровень — это поддержка оркестрации контейнеров, в рамках которой добавляются соответствующие файлы поддержки для определенного оркестратора по выбору.  

В Visual Studio 2017 в качестве служб оркестрации контейнеров можно использовать Docker Compose и Service Fabric.  Кроме того, вы можете применить Kubernetes, если установить [Средства Visual Studio для Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).

> [!NOTE]
> Если вы используете версию Visual Studio 2017, предшествующую 15.8, или шаблон проекта .NET Framework (не .NET Core), при добавлении поддержки Docker поддержка оркестрации с помощью Docker Compose добавляется автоматически. Поддержка оркестрации контейнеров с помощью Docker Compose автоматически добавляется в Visual Studio 2017 в версиях с 15.0 по 15.7, а также в проектах .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Предварительные требования

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с рабочей нагрузкой **Веб-разработка**, **Средства Azure** и (или) **Кроссплатформенная разработка .NET Core**.
* [Средства разработки .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) для разработки с использованием .NET Core.
* Для публикации в Реестр контейнеров Azure требуется подписка Azure. [Зарегистрируйтесь для получения бесплатной пробной версии](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Поддержка Docker в Visual Studio

Поддержка Docker доступна в проектах ASP.NET, ASP.NET Core и консольных проектах .NET Core и .NET Framework.

Поддержка Docker в Visual Studio оптимизировалась с каждым выпуском программы с учетом пожеланий пользователей. Есть два уровня поддержки Docker, которые можно добавить в проект. Набор поддерживаемых возможностей зависит от типа проекта и версии Visual Studio. Если вам необходим контейнер для работы над отдельным проектом, а не оркестрация, для некоторых типов проектов можно просто добавить поддержку Docker.  Следующий уровень — это поддержка оркестрации контейнеров, в рамках которой добавляются соответствующие файлы поддержки для определенного оркестратора по выбору.  

В Visual Studio 2019 в качестве служб оркестрации контейнеров можно использовать Docker Compose, Kubernetes и Service Fabric.

> [!NOTE]
> Если вы используете полный шаблон консольного проекта .NET Framework, после создания проекта поддерживается вариант **Добавление поддержки оркестратора контейнеров** с возможностью использования Service Fabric или Docker Compose. Варианты добавления поддержки при создании проекта и **добавления поддержки Docker** для одного проекта без оркестрации недоступны.

В Visual Studio 2019 версии 16.4 и более поздних версиях доступно окно **Контейнеры**, которое позволяет просматривать запущенные контейнеры, доступные образы, переменные среды, журналы и сопоставления портов, проверять файловую систему, подключать отладчик или открывать окно терминала в среде контейнера. См. статью [Сведения о просмотре и диагностике контейнеров и образов в Visual Studio](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Добавление поддержки Docker

Поддержку Docker можно включить при создании проекта, выбрав **Enable Docker Support** (Включить поддержку Docker), как показано на следующем снимке экрана:

::: moniker range="vs-2017"
![Включение поддержки Docker для нового веб-приложения ASP.NET Core в Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Включение поддержки Docker для нового веб-приложения ASP.NET Core в Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Для проектов .NET Framework (не .NET Core) доступны только контейнеры Windows.

Можно добавить поддержку Docker в существующий проект, выбрав **Добавить** > **Поддержка Docker** в **обозревателе решений**. Для проектов ASP.NET Core команды **Добавить > Поддержка Docker** и **Добавить > Поддержка оркестратора контейнеров** доступны в контекстном меню, открываемом правым щелчком мыши по узлу проекта в ** обозревателе решений**, как показано на следующем снимке экрана:

![Добавление поддержки Docker из меню в Visual Studio](./media/overview/add-docker-support-menu.png)

При добавлении или включении поддержки Docker Visual Studio добавляет в проект следующее:

- файл *Dockerfile*;
- файл .dockerignore;
- ссылку пакета NuGet на Microsoft.VisualStudio.Azure.Containers.Tools.Targets.

::: moniker range=">=vs-2019"
После добавления поддержки Docker решение выглядит следующим образом:

![Снимок экрана обозревателя решений с файлами Dockerfile и .dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Если вы включаете поддержку Docker при создании проекта ASP.NET (проекта .NET Framework, а не .NET Core), как показано на приведенном ниже снимке экрана, при этом добавляется поддержка оркестрации контейнеров.

![Включение поддержки Docker Compose для проекта ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Поддержка Docker Compose

Если требуется создать многоконтейнерное решение с помощью Docker Compose, добавьте в проекты поддержку оркестрации контейнеров. Это позволит выполнять и отлаживать группу контейнеров (всего решения или группы проектов) одновременно, если они определяются в одном файле *docker-compose.yml*.

Чтобы добавить поддержку оркестрации контейнеров с помощью Docker Compose, щелкните правой кнопкой мыши узел решения или проекта в **обозревателе решений** и выберите **Добавить > Поддержка оркестратора контейнеров**. Затем выберите **Docker Compose** для управления контейнерами.

После добавления поддержки оркестрации контейнеров в проект в него добавится файл *Dockerfile* (если его не было прежде), а в само решение — папка **docker-compose**, как показано на следующем снимке экрана **обозревателя решений**:

![Файлы Docker в обозревателе решений Visual Studio](media/overview/docker-support-solution-explorer.png)

Если файл *docker-compose.yml* уже существует, Visual Studio просто добавит в него необходимые строки кода конфигурации.

Повторите этот процесс с другими проектами, которыми нужно управлять с помощью Docker Compose.

## <a name="kubernetes-support"></a>Поддержка Kubernetes

::: moniker range="vs-2017"
Чтобы добавить поддержку Kubernetes, установите [Средства Visual Studio для Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).
::: moniker-end

Поддержка Kubernetes позволяет подключить локальный проект к кластеру Kubernetes, работающему в [Службе Azure Kubernetes (AKS)](/azure/aks), а также изменять и отлаживать работу служб, запущенных в AKS, с помощью Visual Studio.  Эту возможность обеспечивает [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio). В целях разработки Azure Dev Spaces также позволяет настраивать отдельные ветви служб, именуемые *пространствами разработки*. Это дает возможность изолировать рабочие службы от разрабатываемых версий и четко разграничивать отдельные версии.

Чтобы добавить в проекты поддержку Kubernetes, при добавлении поддержки оркестрации контейнеров выберите **Kubernetes/Helm**. В проект будет добавлено несколько файлов, включая *azds.yaml*, который настраивает Azure Dev Spaces и чарты Helm с описанием структуры служб Kubernetes.

## <a name="service-fabric-support"></a>Поддержка Service Fabric

Средства Service Fabric для Visual Studio позволяют выполнять разработку и отладку в локальной среде и Azure Service Fabric, а также развертывание в Azure.

::: moniker range="vs-2017"
Visual Studio 2017 версии 15.9 и более поздних версий с установленной рабочей нагрузкой разработки Azure поддерживает разработку контейнерных микрослужб с помощью контейнеров Windows и оркестрации Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 поддерживает разработку контейнерных микрослужб с помощью контейнеров Windows и оркестрации Service Fabric.
::: moniker-end

Подробные инструкции см. в [руководстве по развертыванию приложения .NET в контейнере Windows в Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Дополнительные сведения см. в [документации по Azure Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Непрерывная интеграция и непрерывное развертывание (CI/CD)

Visual Studio легко интегрируется с Azure Pipelines для автоматической и непрерывной интеграции и поставки изменений в код и настройки служб. Чтобы приступить к работе, см. статью о [создании конвейера](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2).

Сведения касательно Service Fabric см. в [руководстве по развертыванию приложения ASP.NET Core в Azure Service Fabric с помощью Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric).

Сведения касательно Kubernetes см. в статье о [развертывании приложения из контейнера Docker в Службе Azure Kubernetes](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops).

## <a name="next-steps"></a>Дальнейшие действия

Чтобы получить дополнительные сведения о реализации служб и использовании средств Visual Studio для работы с контейнерами, ознакомьтесь со следующими статьями:

[Отладка приложений в локальном контейнере Docker](edit-and-refresh.md)

[Развертывание контейнера ASP.NET в реестр контейнеров из Visual Studio](hosting-web-apps-in-docker.md)
