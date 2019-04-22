---
title: Средства Visual Studio для контейнеров в Windows
description: Изучите средства, доступные в Visual Studio для работы с Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 4b03ccddadf954b8430b7ad9b5a4ed765fccc3f5
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59538062"
---
# <a name="container-tools-in-visual-studio"></a>Средства для контейнеров в Visual Studio

Доступные в Visual Studio средства для разработки с помощью контейнеров просты в использовании и значительно упрощают сборку, отладку и развертывание контейнерных приложений. Можно работать над одним проектом с использованием контейнера или применять оркестрацию контейнеров с Service Fabric, Docker Compose либо Kubernetes для работы с несколькими службами в контейнерах.

> [!NOTE]
> Эта статья касается только использования Visual Studio в Windows. В ней не рассматривается Visual Studio для Mac.

> [!TIP]
> Дополнительные сведения об установке Docker для Windows см. в статье о [Docker для Windows](https://docs.docker.com/docker-for-windows/).

## <a name="docker-support-in-visual-studio"></a>Поддержка Docker в Visual Studio

Некоторые типы проектов .NET обеспечивают поддержку Docker.  Она доступна в проектах ASP.NET, ASP.NET Core и консольных проектах .NET Core и .NET Framework.

Поддержка Docker в Visual Studio оптимизировалась с каждым выпуском программы с учетом пожеланий пользователей. Есть два уровня поддержки Docker, которые можно добавить в проект. Набор поддерживаемых возможностей зависит от типа проекта и версии Visual Studio. Если вам необходим контейнер для работы над отдельным проектом, а не оркестрация, для некоторых типов проектов можно просто добавить поддержку Docker.  Следующий уровень — это поддержка оркестрации контейнеров, в рамках которой добавляются соответствующие файлы поддержки для определенного оркестратора по выбору.  

::: moniker range="vs-2017"

В Visual Studio 2017 в качестве служб оркестрации контейнеров можно использовать Docker Compose и Service Fabric.  Кроме того, вы можете применить Kubernetes, если установить [Средства Visual Studio для Kubernetes](https://aka.ms/get-vsk8stools).

> [!NOTE]
> Если вы используете версию Visual Studio 2017, предшествующую 15.8, или шаблон проекта .NET Framework (не .NET Core), при добавлении поддержки Docker поддержка оркестрации с помощью Docker Compose добавляется автоматически. Поддержка оркестрации контейнеров с помощью Docker Compose автоматически добавляется в Visual Studio 2017 в версиях с 15.0 по 15.7, а также в проектах .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

В Visual Studio 2019 в качестве служб оркестрации контейнеров можно использовать Docker Compose, Kubernetes и Service Fabric.

> [!NOTE]
> Если вы используете полный шаблон проекта консоли .NET Framework, при добавлении поддержки Docker автоматически добавляется поддержка оркестрации с помощью Docker Compose.
::: moniker-end

Для проектов ASP.NET Core команды **Добавить > Поддержка Docker** и **Добавить > Поддержка оркестратора контейнеров** доступны в контекстном меню, открываемом правым щелчком мыши по узлу проекта в  **обозревателе решений**, как показано на следующем снимке экрана:

![Добавление поддержки Docker из меню в Visual Studio](./media/overview/add-docker-support-menu.png)

### <a name="adding-docker-support-without-orchestration"></a>Добавление поддержки Docker (без оркестрации)

Можно добавить поддержку Docker в существующий проект, выбрав **Добавить** > **Поддержка Docker** в **обозревателе решений**. Поддержку Docker можно также включить при создании проекта, выбрав **Enable Docker Support** (Включить поддержку Docker), как показано на следующем снимке экрана:

::: moniker range="vs-2017"
![Включение поддержки Docker для нового веб-приложения ASP.NET Core в Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Включение поддержки Docker для нового веб-приложения ASP.NET Core в Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

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
Чтобы добавить поддержку Kubernetes, установите [Средства Visual Studio для Kubernetes](https://aka.ms/get-vsk8stools).
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

## <a name="next-steps"></a>Следующие шаги

Чтобы получить дополнительные сведения о реализации служб и использовании средств Visual Studio для работы с контейнерами, ознакомьтесь со следующими статьями:

[Отладка приложений в локальном контейнере Docker](vs-azure-tools-docker-edit-and-refresh.md)

[Deploy an ASP.NET container to a container registry using Visual Studio](vs-azure-tools-docker-hosting-web-apps-in-docker.md) (Развертывание контейнера ASP.NET в реестр контейнеров с использованием Visual Studio)
