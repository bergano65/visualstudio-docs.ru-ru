---
title: Как использовать настраиваемый веб-канал NuGet в подключенной среде | Документация Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Используйте настраиваемый веб-канал NuGet, чтобы получить доступ к пакетам NuGet и использовать их в подключенной среде.
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: 71fcf1c3cfb37d783de13514f6a048c3b3711a53
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031225"
---
#  <a name="use-a-custom-nuget-feed-in-a-connected-environment"></a>Использование настраиваемого веб-канала NuGet в подключенной среде

Веб-канал NuGet обеспечивает удобный способ для включения источников пакетов в проект. Служба "Подключенная среда" должна иметь доступ к этому веб-каналу для правильной установки зависимостей в контейнере Docker.

Чтобы настроить веб-канал NuGet, сделайте следующее:
1. Добавьте [ссылку на пакет](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files) в файл `*.csproj` в узле `PackageReference`.

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. Создайте файл [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) в папке проекта.
     * Чтобы добавить ссылку на расположение веб-канала NuGet, используйте раздел `packageSources`. Важно! Веб-канал NuGet должен быть общедоступным.
     * Чтобы настроить имя пользователя и пароль, используйте раздел `packageSourceCredentials`. 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. Если используется система управления версиями, сделайте следующее:
    - Добавьте ссылку на файл `NuGet.Config` в файл `.gitignore`, чтобы случайно не зафиксировать учетные данные в исходном репозитории.
    - Откройте файл `vsce.yaml` в проекте и найдите раздел `build`. Затем вставьте приведенный ниже фрагмент кода для синхронизации файла `NuGet.Config` с Azure, чтобы использовать его при создании образа контейнера (по умолчанию служба "Подключенная среда" не выполняет синхронизацию файлов, которые соответствуют правилам `.gitignore` и `.dockerignore`).

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## <a name="next-steps"></a>Следующие шаги

Когда вы выполните все приведенные выше инструкции, при следующем запуске `vsce up` (или нажатии клавиши `F5` в Visual Studio или VSCode) служба "Подключенная среда" синхронизирует файл `NuGet.Config` с Azure. Этот файл затем будет использоваться `dotnet restore` для установки зависимостей пакета в контейнере.

