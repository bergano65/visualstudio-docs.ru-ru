---
title: Устранение неполадок | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: troubleshooting
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: b41d228bcced6149c95b09b2445dd656ed9772d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31901021"
---
# <a name="troubleshooting-guide"></a>Руководство по устранению неполадок

## <a name="error-upstream-connect-error-or-disconnectreset-before-headers"></a>Ошибка "ошибка подключения к вышестоящему объекту или отключение/сброс до заголовков"
Эта ошибка может возникать при попытке доступа к службе. Например, при переходе по URL-адресу службы в браузере. 

**Причина.** Порт контейнера недоступен. Ниже приведены наиболее распространенные причины. 
* Контейнер еще находится в процессе сборки и развертывания. Это может случиться, если вы запускаете `vsce up` или отладчик, а затем пытаетесь получить доступ к контейнеру до его успешного развертывания.
* Разная конфигурация порта в Dockerfile, диаграмме Helm и серверном коде, который открывает порт.

**Варианты решения.**
1. Если контейнер находится в процессе сборки и развертывания, подождите 2–3 секунды и повторите попытку доступа к службе. 
1. Проверьте конфигурацию порта. Номера порта должны **совпадать** во всех следующих ресурсах:
    * **Dockerfile:** задается инструкцией `EXPOSE`.
    * **[Диаграмма Helm](https://docs.helm.sh):** задается значениями `externalPort` и `internalPort` для службы (часто находится в файле `values.yml`).
    * Все порты, открытые в коде приложения, например в Node.js: `var server = app.listen(80, function () {...}`


## <a name="config-file-not-found"></a>Файл конфигурации не найден
Вы запускаете `vsce up` и видите следующую ошибку: `Config file not found: .../vsce.yaml`

**Причина.** `vsce up` должен запускаться из корневого каталога кода, который вы хотите запустить, и папка с кодом должна быть инициализирована для запуска в подключенной среде.

**Варианты решения.**
1. Измените текущий каталог на корневую папку с кодом службы. 
1. Если у вас нет файла vsce.yaml в папке кода, запустите `vsce init`, чтобы создать ресурсы Docker, Kubernetes и VSCE.

## <a name="error-the-pipe-program-vsce-exited-unexpectedly-with-code-126"></a>Ошибка: "Программа vsce неожиданно закрылась с кодом 126".
Это сообщение иногда возникает при запуске отладчика VS Code. Это ошибка.

**Варианты решения.**
1. Закройте и снова откройте VS Code.
2. Еще раз нажмите клавишу F5.


## <a name="debugging-error-configured-debug-type-coreclr-is-not-supported"></a>Ошибка отладки "Настроенный тип отладки coreclr не поддерживается"
При запуске отладчика VS Code возникает ошибка: `Configured debug type 'coreclr' is not supported.`

**Причина.** На компьютере, на котором ведется разработка, не установлено расширение VS Code для подключенной среды.

**Варианты решения.** Установите [расширение VS Code для подключенной среды](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="the-azure-portal-doesnt-show-connected-environment-instances"></a>На портале Azure не отображаются все экземпляры подключенной среды

**Причина.** Интерфейс портала Azure для подключенной среды еще не готов для предварительного просмотра.


## <a name="the-type-or-namespace-name-mylibrary-could-not-be-found"></a>Не удалось найти имя типа или пространства имен MyLibrary

**Причина.** Контекст сборки находится на уровне проекта или службы по умолчанию, поэтому используемый проект библиотеки не может быть найден.

**Варианты решения.** Что нужно сделать.
1. Измените файл vsce.yaml, чтобы задать контекст сборки на уровне решения.
2. Измените файлы Dockerfile и Dockerfile.develop, чтобы они корректно обращались к файлам csproj в зависимости от нового контекста сборки.
3. Поместите файл .dockerignore рядом с SLN-файлом и внесите необходимые изменения.

Пример: https://github.com/sgreenmsft/buildcontextsample

## <a name="microsoftconnectedenvironmentregisteraction-authorization-error-when-creating-an-environment"></a>Ошибка авторизации при создании среды "Microsoft.ConnectedEnvironment/register/action"
Эта ошибка может возникнуть при управлении средой, когда вы работаете по подписке Azure и не имеете прав владельца или участника.
`The client '<User email/Id>' with object id '<Guid>' does not have authorization to perform action 'Microsoft.ConnectedEnvironment/register/action' over scope '/subscriptions/<Subscription Id>'.`

**Причина.** В выбранной подписке Azure не зарегистрировано пространство имен Microsoft.ConnectedEnvironment.

**Варианты решения.** Пользователь с правами владельца или участника в подписке Azure может выполнить следующую команду Azure CLI, чтобы вручную зарегистрировать пространство имен Microsoft.ConnectedEnvironment:

```cmd
az provider register --namespace Microsoft.ConnectedEnvironment
```

## <a name="vsce-doesnt-seem-to-use-my-existing-dockerfile-to-build-a-container"></a>VSCE не использует существующий Dockerfile для сборки контейнера 

**Причина.** В VSCE можно указать ссылку на определенный Dockerfile в вашем проекте. Если VSCE не использует нужный Dockerfile для сборки контейнеров, вы можете явно указать его расположение. 

**Варианты решения.** Откройте файл `vsce.yaml`, созданный VSCE в вашем проекте. Используйте директиву `configurations->develop->build->dockerfile`, чтобы указать на нужный Dockerfile:

```
...
configurations:
  develop:
    build:
      dockerfile: Dockerfile.develop
```