---
title: Учебник по Средствам для Kubernetes | Документация Майкрософт
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 931f8c2a6d3be130ef78f59f9b3853d28fad8cd4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444691"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Начало работы со Средствами Visual Studio для Kubernetes

Средства Visual Studio для Kubernetes помогают упростить разработку контейнерных приложений, предназначенных для Kubernetes. Visual Studio может автоматически создавать файлы с кодом конфигурации, необходимые для поддержки развертывания Kubernetes, например файлы Dockerfile и диаграммы Helm. Вы можете отлаживать код в активном кластере Службы Azure Kubernetes (AKS) с помощью Azure Dev Spaces или выполнять публикацию непосредственно в кластере AKS из Visual Studio.

В этом руководстве рассматривается использование Visual Studio для добавления поддержки Kubernetes в проект и публикации в AKS. Если вы заинтересованы в первую очередь в использовании [Azure Dev Spaces](/azure/dev-spaces/) для отладки и тестирования проекта, работающего в AKS, то можете перейти к [руководству по Azure Dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio).

## <a name="prerequisites"></a>предварительные требования

Чтобы использовать эту новую функциональность, вам потребуется:

::: moniker range="vs-2017"
- последняя версия [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) с рабочей нагрузкой *ASP.NET и разработка веб-приложений*;
- [Средства Visual Studio для Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), которые можно скачать отдельно;
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с рабочей нагрузкой *ASP.NET и веб-разработка*.
::: moniker-end
- приложение [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows), установленное на рабочей станции разработки (где выполняется Visual Studio), если вы хотите создавать образы Docker, отлаживать контейнеры Docker локально или выполнять публикацию в AKS. (Docker *не* требуется для сборки и отладки контейнеров Docker в AKS с помощью Azure Dev Spaces.)
::: moniker range="vs-2017"
- Если необходимо выполнять публикацию в AKS из Visual Studio (*не* требуется для отладки в AKS с помощью Azure Dev Spaces):

    1. [Средства публикации AKS](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), которые можно скачать отдельно.

    1. Кластер Службы Azure Kubernetes. Дополнительные сведения см. в статье [Создание кластера AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). [Подключитесь к кластеру](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) с рабочей станции разработки.

    1. Установленный интерфейс командной строки Helm на рабочей станции разработки. Дополнительные сведения об установке Helm см. в [этой статье](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md).

    1. Средство Helm, настроенное для кластера AKS с помощью команды `helm init`. Дополнительные сведения о настройке Helm см. в [этой статье](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Создание проекта Kubernetes

::: moniker range="vs-2017"

Установив нужные средства, запустите Visual Studio и создайте проект. В разделе **Облако** выберите тип проекта **Приложение-контейнер для Kubernetes**. Выберите этот тип проекта и нажмите кнопку **ОК**.

![Снимок экрана: создание проекта приложения Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

В начальном окне Visual Studio выполните поиск по запросу *Kubernetes* и выберите **Приложение-контейнер для Kubernetes**.

![Снимок экрана: создание проекта приложения Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Укажите имя проекта.

![Снимок экрана: создание проекта приложения Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

После этого можно выбрать тип веб-приложения ASP.NET Core, которое нужно создать. Выберите **Веб-приложение**. В этом диалоговом окне нет обычного параметра **Включение поддержки Docker**.  Для приложения-контейнера для Kubernetes поддержка Docker включается по умолчанию.

::: moniker range="vs-2017"

![Снимок экрана: выбор веб-приложения](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Снимок экрана: выбор веб-приложения](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Добавление поддержки Kubernetes в существующий проект

Вы также можете добавить поддержку Kubernetes в существующий проект веб-приложения ASP.NET Core. Для этого щелкните проект правой кнопкой мыши и выберите пункт **Добавить** > **Container Orchestrator Support** (Поддержка оркестратора контейнеров).

::: moniker range="vs-2017"

![Снимок экрана: пункт меню для добавления оркестратора контейнеров](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Снимок экрана: пункт меню для добавления оркестратора контейнеров](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

В диалоговом окне выберите **Kubernetes/Helm** и нажмите кнопку **ОК**.

![Снимок экрана: диалоговое окно для добавления оркестратора контейнеров](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Компоненты, создаваемые Visual Studio

После создания проекта **приложения-контейнера для Kubernetes** или добавления поддержки оркестратора контейнеров Kubernetes в существующий проект вы увидите в проекте ряд дополнительных файлов, которые упрощают развертывание в Kubernetes.

::: moniker range="vs-2017"

![Снимок экрана: обозреватель решений после добавления поддержки оркестратора контейнеров](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Снимок экрана: обозреватель решений после добавления поддержки оркестратора контейнеров](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Добавляются перечисленные ниже файлы.

- Файл Dockerfile, который позволяет создать образ контейнера Docker для размещения веб-приложения. Как вы увидите, средства Visual Studio используют этот файл при отладке и развертывании в Kubernetes. Если вы предпочитаете работать непосредственно с образом Docker, то можете щелкнуть Dockerfile правой кнопкой мыши и выбрать пункт **Сборка образа Docker**.

   ![Снимок экрана: пункт "Сборка образа Docker"](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- Диаграмма Helm и папка *charts*. Эти YAML-файлы образуют диаграмму Helm для приложения, которую можно использовать для его развертывания в Kubernetes. Дополнительные сведения о Helm см. на сайте [https://www.helm.sh](https://www.helm.sh).

- *azds.yaml*. Содержит параметры для службы Azure Dev Spaces, обеспечивающей быструю итеративную отладку в Службе Azure Kubernetes. Дополнительные сведения см. в [документации по Azure Dev Spaces](/azure/dev-spaces/azure-dev-spaces).

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Публикация в Службе Azure Kubernetes (AKS)

При наличии всех этих файлов можно использовать интегрированную среду разработки Visual Studio для написания и отладки кода приложения обычным образом. Можно также использовать [Azure Dev Spaces](/azure/dev-spaces/) для быстрого запуска и отладки кода, выполняющегося в кластере AKS. Дополнительные сведения см. в [руководстве по Azure Dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio).

Когда код выполняется нужным образом, его можно опубликовать непосредственно из Visual Studio в кластере AKS.

Для этого сначала необходимо еще раз проверить, установлены ли все компоненты, которые описаны в разделе [Предварительные требования](#prerequisites), относящемся к публикации в AKS, и выполнить все действия в командной строке, приведенные по ссылкам. Затем настройте профиль публикации, с помощью которого образ контейнера будет публиковаться в Реестре контейнеров Azure (ACR). После этого AKS сможет извлечь образ контейнера из ACR и развернуть его в кластере.

1. В **обозревателе решений** щелкните *проект* правой кнопкой мыши и выберите пункт **Опубликовать**.

   ![Снимок экрана: пункт меню "Опубликовать"](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. На экране **Публикация** выберите целевой объект публикации **Реестр контейнеров** и следуйте указаниям, чтобы выбрать реестр контейнеров. Если у вас еще нет реестра контейнеров, выберите **Создать реестр контейнеров Azure**, чтобы создать его из Visual Studio. Дополнительные сведения см. в статье [Публикация контейнера в Реестре контейнеров Azure](hosting-web-apps-in-docker.md).

   ![Снимок экрана: окно "Выберите целевой объект публикации"](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. Вернувшись в обозреватель решений, щелкните *решение* правой кнопкой мыши и выберите пункт **Опубликовать в Azure AKS**.

   ![Снимок экрана: пункт меню "Опубликовать в Azure AKS"](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Выберите подписку и кластер AKS, а также только что созданный профиль публикации ACR. Нажмите кнопку **ОК**.

   ![Снимок экрана: окно публикации в AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Откроется экран **Публикация в Azure AKS**.

5. Щелкните ссылку **Настроить Helm**, чтобы обновить командную строку, используемую для установки диаграмм Helm на сервере.

   ![Снимок экрана: ссылка "Настроить Helm"](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Обновление командной строки полезно, если нужно указать пользовательские аргументы командной строки, например другой контекст Kubernetes или имя диаграммы.

   ![Снимок экрана: экран настройки Helm](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Когда все будет готово к развертыванию, нажмите кнопку **Опубликовать**, чтобы опубликовать приложение в AKS.

   ![Снимок экрана: окно публикации в Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Поздравляем! Теперь вы можете использовать все возможности Visual Studio для разработки приложений Kubernetes.

## <a name="next-steps"></a>Дальнейшие действия

Узнайте больше о разработке для Kubernetes в Azure в [документации по AKS](/azure/aks).

Узнайте больше об Azure Dev Spaces в [документации по Azure Dev Spaces](/azure/dev-spaces/).
