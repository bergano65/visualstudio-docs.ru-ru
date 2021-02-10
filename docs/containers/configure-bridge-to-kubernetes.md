---
title: Использование файла KubernetesLocalProcessConfig.yaml для дополнительной настройки Bridge to Kubernetes
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: Описание дополнительных параметров конфигурации для Bridge to Kubernetes в файле KubernetesLocalProcessConfig.yaml
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, AKS, Служба Azure Kubernetes, контейнеры
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jmartens
ms.openlocfilehash: b250454fe5e80ec18f75add92c8c2f653893e994
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867624"
---
# <a name="configure-bridge-to-kubernetes"></a>Настройка Bridge to Kubernetes

Файл `KubernetesLocalProcessConfig.yaml` позволяет реплицировать переменные среды и подключенные файлы, доступные для групп pod в кластере AKS. В файле `KubernetesLocalProcessConfig.yaml` можно задать следующие действия:

* скачивание тома и указание пути к нему в виде переменной среды;
* предоставление доступа к службе, работающей в кластере, для процессов, выполняющихся на компьютере разработчика;
* создание переменной среды с постоянным значением.

Стандартный файл `KubernetesLocalProcessConfig.yaml` не создается автоматически, поэтому его нужно создать вручную в корневой папке проекта.

## <a name="download-a-volume"></a>Скачивание тома

В разделе *env* укажите значения *name* и *value* для каждого скачиваемого тома. *name* — это переменная среды, которая будет использоваться на компьютере разработки. *value* — это имя тома и путь к нему на компьютере разработки. Значение *value* имеет такой формат: *$(volumeMounts:VOLUME_NAME)/PATH/TO/FILES*.

Пример:

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

В приведенном выше примере скачивается том *allow-list* из контейнера, а также указывается расположение и путь для переменной среды *ALLOW_LIST_PATH*. По умолчанию файлы скачиваются во временный каталог на компьютере разработки по указанному пути. В приведенном выше примере *ALLOW_LIST_PATH* имеет значение `/TEMPORARY_DIR/allow-list`. 

> [!NOTE]
> Том скачивается со всем содержимым независимо от заданного пути. Путь используется только для указания переменной среды, используемой на компьютере разработки. Добавление */allow-list* или */path/to/files* в конец маркера не влияет на то, где будет сохранен том. Переменная среды используется только для удобства, если приложению требуется ссылка на определенный файл внутри этого тома.

Вы также можете указать расположение для скачивания подключенного тома на компьютере разработчика, чтобы не использовать временный каталог. В разделе *volumeMounts* укажите значения *name* и *localPath* для каждого расположения. *name* — это имя тома, которое необходимо сопоставить, а *localPath* — это абсолютный путь на компьютере разработчика. Пример:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

В приведенном выше примере в разделе *env* используется запись для скачивания тома, имя которого соответствует записи *default-token-\** , например *default-token-1111* или *default-token-1234-5678-90abcdef*. Если записи соответствуют несколько томов, используется первый соответствующий том. Все файлы скачиваются в папку `/var/run/secrets/kubernetes.io/serviceaccount` на компьютере разработки с использованием записи из раздела *volumeMounts*. Для переменной среды *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* указывается значение `/var/run/secrets/kubernetes.io/serviceaccount`.

## <a name="make-a-service-available"></a>Предоставление доступа к службе

В разделе *env* укажите значения *name* и *value* для каждой службы, которую необходимо сделать доступной на компьютере разработчика. *name* — это переменная среды, которая будет использоваться на компьютере разработки. *value* — это имя службы из кластера и путь. Значение для *value* имеет такой формат: *$(services:SERVICE_NAME)/PATH*.

Пример:

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

В приведенном выше примере служба *myapp1* становится доступной для компьютера разработки, а для переменной среды *MYAPP1_SERVICE_HOST* указывается локальный IP-адрес службы *myapp1* с путем `/api/v1` (например, `127.1.1.4/api/v1`). Доступ к службе *myapp1* можно получить с помощью переменной среды *myapp1* или *myapp1.svc.cluster.local*.

> [!NOTE]
> При предоставлении доступа к службе на компьютере разработки станут доступны все ее объекты независимо от заданного пути. Путь используется только для указания переменной среды, используемой на компьютере разработки.
Можно также сделать доступной службу из определенного доступного пространства имен Kubernetes, используя *$(services:SERVICE_NAME.NAMESPACE_NAME)* . Пример:

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

В приведенном выше примере предоставляется доступ к службе *myapp2* из пространства имен *mynamespace*, доступного на компьютере разработки, а также для переменной среды *MYAPP2_SERVICE_HOST* указывается значение локального IP-адреса службы *myapp2* из пространства имен *mynamespace*.

## <a name="create-an-environment-variable-with-a-constant-value"></a>Создание переменной среды с постоянным значением

В разделе *env* укажите значения *name* и *value* для каждой переменной среды, которую необходимо создать на компьютере разработки. *name* — это переменная среды, которая будет использоваться на компьютере разработки, а *value* — ее значение. Пример:

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

В приведенном выше примере создается переменная среды с именем *DEBUG_MODE* и значением *true*.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>Пример файла KubernetesLocalProcessConfig.yaml

Ниже приведен пример файла `KubernetesLocalProcessConfig.yaml`:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к использованию Bridge to Kubernetes для подключения локального компьютера разработки к кластеру, см. статьи [Использование Bridge to Kubernetes с Visual Studio Code][bridge-to-kubernetes-vs-code] и [Использование Bridge to Kubernetes с Visual Studio][bridge-to-kubernetes-vs].

[bridge-to-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/bridge-to-kubernetes
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
