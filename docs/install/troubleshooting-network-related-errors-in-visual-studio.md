---
title: Устранение неполадок сети или ошибок прокси-сервера
description: Ознакомьтесь с решениями распространенных ошибок сети или прокси-сервера, которые могут возникать при установке или использовании Visual Studio за брандмауэром или прокси-сервером.
ms.date: 02/12/2018
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 569b137d7a0a85f9c124bd1c643c921f1d64c775
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017829"
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Исправление ошибок сети при установке или использовании Visual Studio

У нас есть решения для распространенных ошибок сети или прокси-сервера, которые могут возникать при установке или использовании Visual Studio за брандмауэром или прокси-сервером.

## <a name="error-proxy-authorization-required"></a>Ошибка: "Требуется проверка подлинности на прокси-сервере"

Эта ошибка обычно происходит, когда пользователи подключаются к Интернету через прокси-сервер, который блокирует вызовы Visual Studio к некоторым сетевым ресурсам.

### <a name="to-fix-this-proxy-error"></a>Устранение этой ошибки прокси-сервера

- Перезапустите Visual Studio. Должно появиться диалоговое окно проверки подлинности прокси. Когда в диалоговом окне появится запрос, введите свои учетные данные.

- Если перезапуск Visual Studio не решит проблему, возможно, прокси-сервер не запрашивает учетные данные для адресов http:&#47;&#47;go.microsoft.com, но делает это для адресов &#42;.visualStudio.com. Для таких серверов попробуйте включить в список разрешенных перечисленные ниже URL-адреса, чтобы разблокировать все сценарии входа в Visual Studio:

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- В противном случае из списка разрешенных можно удалить адрес http:&#47;&#47;go.microsoft.com, чтобы при перезапуске Visual Studio диалоговое окно проверки подлинности прокси-сервера открывалось для адреса http:&#47;&#47;go.microsoft.com и конечных точек сервера.

    OR

- Если вы хотите использовать учетные данные по умолчанию для прокси-сервера, сделайте следующее:

  1. Найдите файл **devenv.exe.config** (файл конфигурации devenv.exe) в папке **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** или **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. В файле конфигурации найдите блок `<system.net>` и добавьте следующий код:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#>" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      В `proxyaddress="<http://<yourproxy:port#>` необходимо вставить правильный адрес прокси-сервера в сети.

     OR

- Вы также можете выполнить инструкции, приведенные в записи блога [How to connect through an authenticated Web Proxy](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) (Как подключиться через проверенный веб-прокси), чтобы добавить код, который позволит вам использовать прокси-сервер.

## <a name="error-the-underlying-connection-was-closed"></a>Ошибка: "Используемое соединение было закрыто"

Если вы работаете с Visual Studio в частной сети, где есть брандмауэр, Visual Studio может быть не в состоянии подключиться к некоторым сетевым ресурсам. К таким ресурсам могут относиться Azure DevOps Services для входа и лицензирования, а также NuGet и службы Azure. Если Visual Studio не удается подключиться к одному из этих ресурсов, отображается следующее сообщение об ошибке:

  **Используемое соединение было закрыто: обнаружена неожиданная ошибка при отправке**

Visual Studio использует протокол TLS 1.2 для подключения к сетевым ресурсам. Устройства для обеспечения безопасности в частных сетях блокируют определенные подключения к серверу, если Visual Studio использует TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Устранение этой ошибки подключения

Включите возможность подключения для следующих URL-адресов:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (для подключений к Azure)

- &#42;.visualstudio.com

- cdn.vsassets.io (размещение сети доставки содержимого или CDN)

- &#42;.gallerycdn.vsassets.io (размещает расширение Azure DevOps Services)

- static2.sharepointonline.com (размещение ресурсов, которые Visual Studio использует в комплекте Office UI Fabric, например, шрифтов)

- &#42;.nuget.org (для подключений к NuGet)

  > [!NOTE]
  > Частные URL-адреса серверов NuGet могут быть не включены в этот список. Используемые вами серверы NuGet можно посмотреть в файле %APPData%\Nuget\NuGet.Config.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка и использование Visual Studio в среде, защищенной брандмауэром или прокси-сервером](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Установка Visual Studio 2017](install-visual-studio.md)
