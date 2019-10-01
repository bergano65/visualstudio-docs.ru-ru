---
title: Устранение неполадок клиента Docker в Windows | Документация Майкрософт
description: Устранение неполадок, которые возникают при использовании Visual Studio для создания и развертывания веб-приложений в Docker в Windows с помощью Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 10/13/2017
ms.author: ghogen
ms.openlocfilehash: ca43098740a1e8e940f27eae8d2c4d405c23230b
ms.sourcegitcommit: 16d8ffc624adb716753412a22d586eae68a29ba2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "71125959"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Устранение неполадок при разработке с Docker в Visual Studio

Используя средства Visual Studio для работы с контейнерами, вы можете столкнуться с некоторыми проблемами при создании или отладке приложения. Далее приведены некоторые распространенные действия по устранению неполадок.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Совместное использование тома не включено. Включите совместное использование тома в параметрах Docker CE для Windows (только для контейнеров Linux)

Действия для устранения этой проблемы.

1. Щелкните правой кнопкой мыши **Docker for Windows** (Docker для Windows) в области уведомлений, а затем выберите **Параметры**.
1. Выберите **Shared Drives** (Общие диски) и включите общий доступ для использования системного диска вместе с диском, на котором находится проект.

> [!NOTE]
> Если файлы отображаются как совместно используемые, вам все равно нужно щелкнуть ссылку Reset credentials... (Сбросить учетные данные...) в нижней части диалогового окна, чтобы снова включить общий доступ к тому. Для продолжения работы после сброса учетных данных, возможно, потребуется перезапустить Visual Studio.

![общие диски](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> В версиях позднее Visual Studio 2017 15.6 выдается предупреждение, если **Общие диски** не настроены.

### <a name="container-type"></a>Тип контейнера

При добавлении в проект поддержки Docker выберите контейнер Windows или Linux. Узел Docker должен работать на контейнерах такого же типа. Чтобы изменить тип контейнера для работающего экземпляра Docker, щелкните правой кнопкой мыши значок Docker в области уведомлений и выберите **Переключение на контейнеры Windows** или **Переключение на контейнеры Linux**.

## <a name="unable-to-start-debugging"></a>Невозможно начать отладку

Одна из причин может быть связана с наличием устаревших компонентов отладки в папке профиля пользователя. Чтобы последние компоненты отладки скачались при следующем сеансе отладки, выполните следующие команды для удаления папок:

- del %userprofile%\vsdbg;
- del %userprofile%\onecoremsvsmon.

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Ошибки, характерные для сетей при отладке приложения

Попробуйте выполнить сценарий, который можно скачать из репозитория GitHub для [очистки сетей узлов контейнера](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), который обновит связанные с сетью компоненты на вашем хост-компьютере.

## <a name="mounts-denied"></a>Отказ в подключении

При использовании Docker для macOS может появиться ошибка со ссылкой на папку /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Добавьте папку на вкладку общего доступа к файлам в Docker

## <a name="docker-users-group"></a>Группа пользователей Docker

При работе с контейнерами в Visual Studio может возникнуть следующая ошибка.

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Для работы с контейнерами Docker требуются разрешения, предоставляемые участникам группы docker-users.  Чтобы добавить себя в эту группу в Windows 10, выполните указанные ниже действия.

1. В меню "Пуск" откройте **Управление компьютером**.
1. Разверните узел **Локальные пользователи и группы** и выберите узел **Группы**.
1. Найдите группу **docker-users**, щелкните ее правой кнопкой мыши и выберите пункт **Добавить в группу**.
1. Добавьте свою учетную запись пользователя или несколько учетных записей.
1. Выйдите из системы и войдите снова, чтобы изменения вступили в силу.

Добавлять пользователей в группы можно также с помощью команды `net localgroup` в командной строке администратора.

```cmd
net localgroup docker-users DOMAIN\username /add
```

В PowerShell используйте командлет [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember).

## <a name="microsoftdockertools-github-repo"></a>Репозиторий GitHub Microsoft/DockerTools

При возникновении других проблем дополнительные сведения см. в репозитории [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).