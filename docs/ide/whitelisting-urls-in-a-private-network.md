---
title: "Добавление URL-адресов в список разрешений в частной сети | Документы Майкрософт"
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 94348821e44b5ed07e3df5e4859796342919a833
ms.sourcegitcommit: cc288456329aefca1fdaa7ce74751ce195985c14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="whitelisting-urls-in-a-private-network"></a>Добавление URL-адресов в список разрешений в частной сети

Если вы работаете с Visual Studio в частной сети, где используется устройство безопасности, например брандмауэр, Visual Studio может быть не в состоянии подключиться к некоторым сетевым ресурсам. К таким ресурсам относятся Visual Studio Team Services (VSTS) для входа и лицензирования, службы Azure и NuGet. Если Visual Studio не удается подключиться к одному из этих ресурсов, отображается следующее сообщение об ошибке:

  **Базовое соединение закрыто: непредвиденная ошибка при передаче**

Visual Studio использует протокол TLS 1.2 для подключения к сетевым ресурсам. Устройства для обеспечения безопасности в частных сетях блокируют определенные подключения к серверу, если Visual Studio использует TLS 1.2. Чтобы исправить ошибку, включите подключения для следующих URL-адресов:

- https://management.core.windows.net.

- https://app.vssps.visualstudio.com.

- https://login.microsoftonline.com.

- https://login.live.com.

- https://go.microsoft.com.

- https://graph.windows.net.

- https://app.vsspsext.visualstudio.com.

- *.azurewebsites.net (для подключений к Azure)

- *.nuget.org (для подключений к NuGet)

- *.visualstudio.com

- cdn.vsassets.io (размещение сети доставки содержимого или CDN)

- *.gallerycdn.vsassets.io (размещение расширений VSTS)

- static2.sharepointonline.com (размещение ресурсов, которые Visual Studio использует в комплекте пользовательского интерфейса для офисной структуры, например, шрифтов)

> [!NOTE]
> Частные URL-адреса серверов NuGet могут быть не включены в приведенный выше список. Чтобы узнать, какие серверы NuGet используются вами, откройте файл %APPData%\Nuget\NuGet.Config.

## <a name="see-also"></a>См. также

[Ошибка запроса проверки подлинности на прокси-сервере](../ide/reference/proxy-authorization-required.md)  
[Ресурсы в Интернете, используемые Visual Studio](../ide/connected-environment.md)  
[Установка Visual Studio в среде, защищенной брандмауэром или прокси-сервером](../install/install-visual-studio-behind-a-firewall-or-proxy-server.md)
