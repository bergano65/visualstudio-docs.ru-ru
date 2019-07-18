---
title: Требуется проверка подлинности на прокси-сервере | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2de40c520bca0ea04f50ec782fec2dda531172e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67822073"
---
# <a name="proxy-authorization-required"></a>Требуется проверка подлинности на прокси-сервере
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Требуется проверка подлинности на прокси-сервера** ошибка обычно возникает, когда пользователи подключены к Visual Studio online ресурсам через прокси-сервера и прокси-сервер блокирует вызовы.

Чтобы исправить эту ошибку, выполните одно или несколько из следующих действий:

- Перезапустите Visual Studio. Должно появиться диалоговое окно проверки подлинности прокси. Введите в диалоговом окне свои учетные данные.

- Если приведенное выше действие не помогло решить проблему, возможно, прокси-сервер не запрашивает учетные данные для адресов http://go.microsoft.com, но запрашивает для адресов *.visualStudio.com. Для таких серверов необходимо добавить следующие URL-адреса в список разрешений, чтобы разблокировать все сценарии входа в систему, в Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- Вы можете удалить http://go.microsoft.com адрес из списка, чтобы диалоговое окно проверки подлинности прокси открывалось для обоих http://go.microsoft.com адрес и конечные точки сервера при запуске Visual Studio.

- Если вы хотите использовать учетные данные по умолчанию с помощью прокси-сервер, сделайте следующее:

   1. Найдите файл devenv.exe.config (файл конфигурации devenv.exe) в папке **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (или **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. В файле конфигурации найдите блок `<system.net>` и добавьте следующий код:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Вставьте адрес прокси-сервера для сети в `proxyaddress="<http://<yourproxy:port#>`.

- Следуйте инструкциям в [этой записи блога](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) добавить код, который позволяет вам использовать прокси-сервер.
