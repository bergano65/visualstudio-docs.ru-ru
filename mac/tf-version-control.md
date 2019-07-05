---
title: Система управления версиями Team Foundation (TFVC)
description: Подключение Visual Studio для Mac к Team Foundation Server или Azure DevOps с использованием системы управления версиями Team Foundation (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 06/25/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 04a251621af1086c15bafa15b7a9fe01f8dab5a8
ms.sourcegitcommit: 9d3529e40438ca45dcb0b31742c4cd5a89daa61e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398986"
---
# <a name="connecting-to-team-foundation-version-control"></a>Подключение к системе управления версиями Team Foundation

> [!NOTE]
> Для получения наилучших результатов управления версиями в macOS вместо системы управления версиями Team Foundation (TFVC) рекомендуется использовать Git. Git поддерживается в Visual Studio для Mac и является параметром по умолчанию для репозиториев, размещенных в Team Foundation Server (TFS) или Azure DevOps. Дополнительные сведения об использовании Git с TFS или Azure DevOps см. в статье [Настройка репозитория Git](/visualstudio/mac/set-up-git-repository).
> 
> Расширение TFVC для Visual Studio для Mac, которое вы могли ранее использовать в предварительной версии, больше не поддерживается в Visual Studio 2019 для Mac.

Azure Repos предоставляет две модели управления версиями: [Git](/azure/devops/repos/git/?view=azure-devops), распределенную систему контроля версий, и [систему управления версиями Team Foundation](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), централизованную систему контроля версий.

Visual Studio для Mac обеспечивает полную поддержку репозиториев Git, но требует некоторых обходных путей для работы с TFVC. Если на сегодняшний день для управления версиями вы используете TFVC, ниже приведены несколько решений, которые можно использовать для доступа к исходному коду, размещенному в TFVC:

* [Использование Visual Studio Code и расширения Azure Repos для графического пользовательского интерфейса.](#use-visual-studio-code-and-the-azure-repos-extension)
* [Подключение к репозиторию с помощью клиента командной строки Team Explorer Everywhere (TEE-CLC).](#connecting-using-the-team-explorer-everywhere-command-line-client)

Перечисленные выше параметры будут рассмотрены в последующих разделах этой статьи.

## <a name="requirements"></a>Требования

* Visual Studio Community, Professional или Enterprise для Mac версии 7.8 или более поздней.
* Azure DevOps, Team Foundation Server 2013 или более поздней версии или Azure DevOps Services 2018 или более поздней версии.
* Проект в Azure DevOps или Team Foundation Server и Azure DevOps Server, настроенный на использование системы управления версиями Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Использование Visual Studio Code и расширения Azure Repos

Если вы предпочитаете работать с графическим интерфейсом для управления файлами в системе управления версиями, в таком случае корпорация Майкрософт предоставляет поддерживаемое решение для расширения Azure Repos для Visual Studio Code. Чтобы приступить к работе, загрузите [Visual Studio Code](https://code.visualstudio.com) и узнайте, как [настроить расширение Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Подключение с помощью клиента командной строки Team Explorer Everywhere

Если вы предпочитаете использовать Терминал macOS, в таком случае клиент командной строки Team Explorer Everywhere (TEE-CLC) предоставит поддерживаемый способ подключения к вашему источнику в TFVC.

Чтобы настроить подключение к TFVC и зафиксировать изменения, вы можете выполнить следующие шаги.

### <a name="setting-up-the-tee-clc"></a>Настройка TEE-CLC

Существует два способа настройки TEE-CLC.

* Использовать Homebrew для установки клиента или
* загрузить и установить клиент вручную.

Самым простым решением является **использование Homebrew**, диспетчера пакетов для macOS. Установка с помощью этого метода.

1. Запустите приложение Терминала macOS.
1. Установите Homebrew с помощью Терминала и инструкции на [главной странице Homebrew](https://brew.sh/).
1. После этого выполните следующую команду из Терминала: `brew install tee-clc`

Чтобы **настроить TEE-CLC вручную** выполните следующее.

1. [Загрузите последнюю версию TEE-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) на странице выпусков репозитория Team Explorer Everywhere на GitHub (например, на момент написания этой статьи — это tee-clc-14.134.0.zip).
1. Извлеките содержимое ZIP-файла в папку на диске.
1. Откройте приложение Терминала macOS и используйте команду `cd`, чтобы перейти в папку, которую вы использовали на предыдущем шаге.
1. Выполните команду `./tf` в папке, чтобы проверить рабочее состояние клиента командной строки. Вам может быть предложено установить Java или другие зависимости.

После установки TEE-CLC вы можете выполнить команду `tf eula`, чтобы просмотреть и принять лицензионное соглашение для клиента.

Наконец, для проверки подлинности в вашей среде TFS или Azure DevOps вам необходимо создать личный маркер доступа на сервере. Просмотрите дополнительные сведения о [проверке подлинности с помощью личных маркеров доступа](https://docs.microsoft.com/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). При создании личного маркера доступа для использования с TFVC во время его настройки предоставьте полный доступ.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Использование TEE-CLC для подключения к репозиторию

Чтобы подключиться к исходному коду, необходимо сначала создать рабочую область с помощью команды `tf workspace`. Например, следующие команды подключаются к организации в Azure DevOps, которая называется MyOrganization. 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Параметр среды `TF_AUTO_SAVE_CREDENTIALS` используется для сохранения учетных данных, поэтому их не нужно будет вводить несколько раз. При запросе имени пользователя используйте личный маркер доступа, который был создан в предыдущем разделе, и пустой пароль.

Для создания сопоставления исходных файлов с локальной папкой используйте команду `tf workfold`. В следующем примере будет сопоставлена ​​папка с именем WebApp.Services из проекта TFVC MyRepository и настроена для копирования в локальную папку ~/Projects/ (то есть в папку Projects в домашней папке текущих пользователей).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Наконец используйте следующую команду для получения исходных файлов с сервера и скопируйте их локально.

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Фиксация изменений с помощью TEE-CLC

После внесения изменений в файлы Visual Studio для Mac можно вернутся обратно в окно Терминала для возврата изменений. Команда `tf add` используется для добавления файлов в список ожидающих изменений для возврата, а команда `tf checkin` выполняет фактический возврат к серверу. Команда `checkin` содержит параметры для добавления комментария или сопоставления связанного с ним рабочего элемента. В следующем фрагменте кода все файлы в папке `WebApp.Services` рекурсивно добавляются для возврата после изменений. Затем код проверяется с помощью комментария и связывается с рабочим элементом, который имеет идентификатор "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Чтобы узнать больше об этих или других командах, используйте следующую команду Терминала.

`tf help`

### <a name="see-also"></a>См. также

- [Разработка и совместное использование кода в TFVC с использованием Visual Studio (в Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)