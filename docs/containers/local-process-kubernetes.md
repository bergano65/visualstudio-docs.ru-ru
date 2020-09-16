---
title: Использование Локального процесса с Kubernetes в Visual Studio
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Узнайте, как использовать функцию "Локальный процесс с Kubernetes" в Visual Studio для подключения компьютера разработчика к кластеру Kubernetes.
keywords: Локальный процесс с Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, контейнеры
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: 62b07affd1e54b0dfa8127ecf57626e90ed7dd0e
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037449"
---
# <a name="use-local-process-with-kubernetes-preview"></a>Использование Локального процесса с Kubernetes (предварительная версия)

Локальный процесс с Kubernetes позволяет выполнять и отлаживать код на компьютере разработки, подключенном к кластеру Kubernetes, в котором находятся остальные приложения или службы. Например, при наличии масштабной архитектуры микрослужб со множеством взаимозависимых служб и баз данных репликация этих зависимостей на компьютере разработки может представлять сложность. Кроме того, сборка и развертывание кода в кластере Kubernetes при каждом изменении кода в процессе внутреннего цикла разработки могут занимать много времени и затруднять использование отладчика.

Функция "Локальный процесс с Kubernetes" избавляет от необходимости выполнять сборку кода и развертывать его в кластере благодаря прямому подключению между компьютером разработки и кластером. Подключение компьютера разработки к кластеру во время отладки позволяет быстро тестировать и разрабатывать службу в контексте полного приложения, не создавая конфигурацию Docker или Kubernetes.

Локальный процесс с Kubernetes перенаправляет трафик между подключенным кластером Kubernetes и компьютером разработки. Это перенаправление трафика позволяет коду на компьютере разработки и службам, работающим в кластере Kubernetes, взаимодействовать так, как если бы они находились в одном кластере Kubernetes. Локальный процесс с Kubernetes также позволяет реплицировать переменные среды и подключенные тома, доступные модулям pod в кластере Kubernetes, на компьютере разработки. Наличие доступа к переменным среды и подключенным томам на компьютере разработки позволяет быстро работать с кодом, не реплицируя эти зависимости вручную.

В этом руководство вы узнаете, как использовать функцию "Локальный процесс с Kubernetes" для перенаправления трафика между кластером Kubernetes и кодом, выполняемым на компьютере разработки. В нем также приводится скрипт для развертывания большого примера приложения с несколькими микрослужбами в кластере Kubernetes.

> [!IMPORTANT]
> Эта функция в настоящее время находится на стадии предварительной версии. Предварительные версии предоставляются при условии, что вы принимаете [дополнительные условия использования][preview-terms]. Некоторые аспекты этой функции могут быть изменены до выхода общедоступной версии.

## <a name="before-you-begin"></a>Подготовка к работе

Для демонстрации подключения компьютера разработки к кластеру Kubernetes в этом руководством используется [пример приложения для аренды велосипедов][bike-sharing-github]. Если у вас уже есть свое приложение в кластере Kubernetes, вы можете выполнить описанные ниже инструкции, используя имена собственных служб.

### <a name="prerequisites"></a>Предварительные требования

* Подписка Azure. Если у вас нет подписки Azure, создайте [бесплатную учетную запись](https://azure.microsoft.com/free).
* [Установленный Azure CLI][azure-cli].
* [Visual Studio 2019][visual-studio] версии 16.7, предварительная версия 4, или более поздней версии в ОС Windows 10 с установленной рабочей нагрузкой *Разработка для Azure*.
* [Установленное расширение "Локальный процесс для Kubernetes"][lpk-extension].

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
chmod +x ./local-process-quickstart.sh
./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
```

Перейдите к примеру приложения, работающему в кластере, открыв его общедоступный URL-адрес, который отображается в выходных данных скрипта установки.

```console
$ ./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
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

Откройте файл *mindaro/samples/BikeSharingApp/ReservationEngine/app.csproj* из [примера приложения для аренды велосипедов][bike-sharing-github] в Visual Studio.

В проекте в раскрывающемся списке параметров запуска выберите *Локальный процесс с Kubernetes*, как показано ниже.

![Выбор параметра "Локальный процесс с Kubernetes"](media/local-process-kubernetes/choose-local-process.png)

Нажмите кнопку запуска рядом с пунктом *Локальный процесс с Kubernetes*. В диалоговом окне *Локальный процесс с Kubernetes* выполните указанные ниже действия.

* Выберите свою подписку.
* Выберите кластер *MyAKS*.
* Выберите пространство имен *dev*.
* Выберите службу *reservationengine* для перенаправления.
* Выберите профиль запуска *app*.
* Выберите URL-адрес `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` для открытия в браузере.

![Выбор кластера для функции "Локальный процесс с Kubernetes"](media/local-process-kubernetes/choose-local-process-cluster.png)

> [!IMPORTANT]
> Перенаправление можно выполнять только для служб с одним модулем pod.

Нажмите кнопку *Сохранить и начать отладку*.

Весь трафик службы *reservationengine* в кластере Kubernetes перенаправляется в версию приложения на компьютере разработки. Функция "Локальный процесс с Kubernetes" также направляет весь исходящий трафик из приложения обратно в кластер Kubernetes.

> [!NOTE]
> Вам будет предложено предоставить *KubernetesDNSManager* повышенные привилегии для изменения файла hosts.

Когда в строке состояния указывается, что установлено подключение к службе *reservationengine*, это означает, что компьютер разработки подключен.

![Компьютер разработки подключен](media/local-process-kubernetes/development-computer-connected.png)

> [!NOTE]
> В дальнейшем при запуске диалоговое окно *Локальный процесс с Kubernetes* выводиться не будет. Параметры можно изменить в области *Отладка* в свойствах проекта.

После подключения компьютера разработки трафик заменяемой службы начинает перенаправляться на него.

## <a name="set-a-break-point"></a>Установка точки останова

Откройте файл [server.js][bikeshelper-cs-breakpoint] и щелкните строку 26, чтобы расположить в ней курсор. Задайте точку останова, нажав клавишу *F9* или щелкнув *Отладка*, а затем *Переключить точку останова*.

Перейдите к примеру приложения по его общедоступному URL-адресу. Выберите пользователя *Aurelia Briggs (customer)* , а затем выберите велосипед, который нужно сдать в прокат. Нажмите кнопку *Rent Bike* (Сдать велосипед в прокат). Вернувшись в Visual Studio, вы увидите, что строка 26 выделена. Заданная вами точка останова приостановила выполнение службы на строке 26. Чтобы возобновить работу службы, нажмите клавишу *F5* или щелкните *Отладка*, а затем *Продолжить*. Вернитесь в браузер и убедитесь в том, что на странице указано, что велосипед сдан в прокат.

Удалите точку останова, поместив курсор в строке 26 в `BikesHelper.cs` и нажав клавишу *F9*.

> [!NOTE]
> По умолчанию при остановке задачи отладки компьютер разработки отключается от кластера Kubernetes. Это поведение можно изменить, изменив значение параметра *Отключиться после отладки* на *false* в разделе *Средства отладки Kubernetes* параметров отладки. После изменения этого параметра компьютер разработки будет оставаться подключенным при остановке и запуске отладки. Чтобы отключить компьютер разработки от кластера, нажмите кнопку *Отключиться* на панели инструментов.
>
> Если Visual Studio внезапно завершает подключение к кластеру или завершает работу, то перенаправляемая служба может не перейти в исходное состояние, в котором она находилась до подключения с помощью функции "Локальный процесс с Kubernetes". Чтобы исправить эту проблему, обратитесь к [руководству по устранению неполадок][troubleshooting].

## <a name="additional-configuration"></a>Дополнительная настройка

Локальный процесс с Kubernetes может обрабатывать трафик маршрутизации и выполнять репликацию переменных среды без дополнительной настройки. Если необходимо скачать файлы, подключенные к контейнеру в кластере Kubernetes, например файл ConfigMap, можно создать `KubernetesLocalProcessConfig.yaml` для скачивания этих файлов на компьютер разработки. Дополнительные сведения см. в статье об [использовании KubernetesLocalProcessConfig.yaml для дополнительной настройки Локального процесса с Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Использование ведения журналов и диагностики

Журналы диагностики находятся в подкаталоге `Local Process with Kubernetes` в каталоге *TEMP* на компьютере разработки. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Удаление примера приложения из кластера

Чтобы удалить пример приложения из кластера, используйте предоставленный скрипт.

```azurecli-interactive
./local-process-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Следующие шаги

Ознакомьтесь с принципами работы функции "Локальный процесс с Kubernetes".

> [!div class="nextstepaction"]
> [Принцип работы функции "Локальный процесс с Kubernetes"](overview-local-process-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-local-process-with-kubernetes.md