---
title: Использование Bridge to Kubernetes с Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Узнайте, как использовать функцию Bridge to Kubernetes в Visual Studio для подключения компьютера разработчика к кластеру Kubernetes.
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, контейнеры
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: 23d060489a13aa8e02316e253d9367e9e3372bbe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859636"
---
# <a name="use-bridge-to-kubernetes"></a>Использование Bridge to Kubernetes

Вы можете использовать функцию Bridge to Kubernetes для перенаправления трафика между кластером Kubernetes и кодом, выполняемым на компьютере разработки. В нем также приводится скрипт для развертывания большого примера приложения с несколькими микрослужбами в кластере Kubernetes.

## <a name="before-you-begin"></a>Подготовка к работе

Для демонстрации подключения компьютера разработки к кластеру Kubernetes в этом руководством используется [пример приложения для аренды велосипедов][bike-sharing-github]. Если у вас уже есть свое приложение в кластере Kubernetes, вы можете выполнить описанные ниже инструкции, используя имена собственных служб.

### <a name="prerequisites"></a>Предварительные требования

* Подписка Azure. Если у вас нет подписки Azure, создайте [бесплатную учетную запись](https://azure.microsoft.com/free).
* [Установленный Azure CLI][azure-cli].
* [Visual Studio 2019][visual-studio] версии 16.7, предварительная версия 4, или более поздней версии в ОС Windows 10 с установленной рабочей нагрузкой *Разработка для Azure*.
* [Установленное расширение Bridge to Kubernetes][btk-extension].

Кроме того, для консольных приложений .NET установите пакет NuGet *Microsoft.VisualStudio.Azure.Kubernetes.Tools.Targets*.

## <a name="create-a-kubernetes-cluster"></a>Создание кластера Kubernetes

Создайте кластер AKS в [поддерживаемом регионе][supported-regions]. Следующие команды создают группу ресурсов *MyResourceGroup* и кластер AKS *MyAKS*.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Установка примера приложения

Установите пример приложения в кластере с помощью предоставленного скрипта. Скрипт можно запустить с помощью [Azure Cloud Shell][azure-cloud-shell].

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

Перейдите к примеру приложения, работающему в кластере, открыв его общедоступный URL-адрес, который отображается в выходных данных скрипта установки.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

В приведенном выше примере используется общедоступный URL-адрес `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Подключение к кластеру и отладка службы

На компьютере разработки скачайте и настройте Kubernetes CLI для подключения к кластеру Kubernetes с помощью команды [az aks get-credentials][az-aks-get-credentials].

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

В репозитории [примера приложения для аренды велосипедов][bike-sharing-github] в GitHub нажмите зеленую кнопку **Code** (Код) и в раскрывающемся списке выберите пункт **Open in Visual Studio** (Открыть в Visual Studio), чтобы клонировать репозиторий на локальный компьютер и открыть папку в Visual Studio. Затем выберите пункт меню **Файл** > **Открыть проект**, чтобы открыть проект **app.csproj** в папке *samples/BikeSharingApp/ReservationEngine*.

В проекте в раскрывающемся списке параметров запуска выберите **Bridge to Kubernetes**, как показано ниже.

![Выбор параметра Bridge to Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Нажмите кнопку запуска рядом с пунктом *Bridge to Kubernetes*. В диалоговом окне **Создание профиля для Bridge to Kubernetes** выполните указанные ниже действия.

* Выберите свою подписку.
* Выберите кластер *MyAKS*.
* Выберите пространство имен *bikeapp*.
* Выберите службу *reservationengine* для перенаправления.
* Выберите профиль запуска *app*.
* Выберите URL-адрес `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` для открытия в браузере.

![Выбор кластера Bridge to Kubernetes](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> Перенаправление можно выполнять только для служб с одним модулем pod.

Выберите, следует ли использовать изолированный режим, в котором ваши изменения не будут влиять на других пользователей, использующих кластер. Режим изоляции реализуется путем маршрутизации ваших запросов к вашей копии каждой затронутой службы. При этом остальной трафик маршрутизируется в обычном режиме. Дополнительные сведения об этом см. в статье [Как работает Bridge to Kubernetes][btk-overview-routing].

Нажмите кнопку **Сохранить и начать отладку**.

Весь трафик службы *reservationengine* в кластере Kubernetes перенаправляется в версию приложения на компьютере разработки. Функция Bridge to Kubernetes также направляет весь исходящий трафик из приложения обратно в кластер Kubernetes.

> [!NOTE]
> Вам будет предложено предоставить *EndpointManager* повышенные привилегии для изменения файла hosts.

Когда в строке состояния указывается, что установлено подключение к службе `reservationengine`, это означает, что компьютер разработки подключен.

![Компьютер разработки подключен](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> В дальнейшем при запуске диалоговое окно **Создание профиля для Bridge to Kubernetes** выводиться не будет. Параметры можно изменить в области **Отладка** в свойствах проекта.

После подключения компьютера разработки трафик заменяемой службы начинает перенаправляться на него.

## <a name="set-a-break-point"></a>Установка точки останова

Откройте файл [server.js][bikeshelper-cs-breakpoint] и щелкните строку 26, чтобы расположить в ней курсор. Задайте точку останова, нажав клавишу *F9* или выбрав пункт меню **Отладка** > **Переключить точку останова**.

Перейдите к примеру приложения по его общедоступному URL-адресу. Выберите пользователя **Aurelia Briggs (customer)** , а затем выберите велосипед, который нужно сдать в прокат. Нажмите кнопку **Rent Bike** (Сдать велосипед в прокат). Вернувшись в Visual Studio, вы увидите, что строка 26 выделена. Заданная вами точка останова приостановила выполнение службы на строке 26. Чтобы возобновить работу службы, нажмите клавишу **F5** или выберите пункт меню **Отладка** > **Продолжить**. Вернитесь в браузер и убедитесь в том, что на странице указано, что велосипед сдан в прокат.

Удалите точку останова, поместив курсор в строке 26 в `BikesHelper.cs` и нажав клавишу **F9**.

> [!NOTE]
> По умолчанию при остановке задачи отладки компьютер разработки отключается от кластера Kubernetes. Это поведение можно изменить, изменив значение параметра **Отключиться после отладки** на `false` в разделе **Средства отладки Kubernetes** параметров отладки. После изменения этого параметра компьютер разработки будет оставаться подключенным при остановке и запуске отладки. Чтобы отключить компьютер разработки от кластера, нажмите кнопку **Отключиться** на панели инструментов.

## <a name="additional-configuration"></a>Дополнительная настройка

Bridge to Kubernetes может обрабатывать трафик маршрутизации и выполнять репликацию переменных среды без дополнительной настройки. Если необходимо скачать файлы, подключенные к контейнеру в кластере Kubernetes, например файл ConfigMap, можно создать `KubernetesLocalProcessConfig.yaml` для скачивания этих файлов на компьютер разработки. Дополнительные сведения см. в статье об [использовании KubernetesLocalProcessConfig.yaml для дополнительной настройки Bridge to Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Использование ведения журналов и диагностики

Журналы диагностики находятся в подкаталоге `Bridge to Kubernetes` в каталоге *TEMP* на компьютере разработки. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Удаление примера приложения из кластера

Чтобы удалить пример приложения из кластера, используйте предоставленный скрипт.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Следующие шаги

Узнайте, как работает Bridge to Kubernetes.

> [!div class="nextstepaction"]
> [Как работает Bridge to Kubernetes](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/overview.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation