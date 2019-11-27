---
title: Требуется проверка подлинности на прокси-сервере | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297821"
---
# <a name="proxy-authorization-required"></a>Требуется проверка подлинности на прокси-сервере
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ошибка **авторизации прокси-** сервера обычно возникает, когда пользователи подключаются к ресурсам Visual Studio Online через прокси-сервер, а прокси-сервер блокирует вызовы.

Чтобы исправить эту ошибку, попробуйте выполнить одно или несколько из следующих действий.

- Перезапустите Visual Studio. Должно появиться диалоговое окно проверки подлинности прокси. Введите в диалоговом окне свои учетные данные.

- Если приведенное выше действие не помогло решить проблему, возможно, прокси-сервер не запрашивает учетные данные для адресов https://go.microsoft.com, но запрашивает для адресов *.visualStudio.com. Для этих серверов необходимо добавить следующие URL-адреса в список разрешений, чтобы разблокировать все сценарии входа в Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualStudio.com

  - *.microsoft.com

  - *.live.com

- Вы можете удалить адрес https://go.microsoft.com из списка разрешений, чтобы диалоговое окно проверки подлинности прокси-сервера выпускалось как для адреса https://go.microsoft.com, так и для конечных точек сервера при перезапуске Visual Studio.

- Если вы хотите использовать учетные данные по умолчанию с прокси-сервером, выполните следующие действия.

   1. Найдите файл devenv.exe.config (файл конфигурации devenv.exe) в папке **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (или **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. В файле конфигурации найдите блок `<system.net>` и добавьте следующий код:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Вставьте правильный прокси-адрес для сети в `proxyaddress="<http://<yourproxy:port#>`.

- Следуйте инструкциям в [этой записи блога](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) , чтобы добавить код, позволяющий использовать прокси-сервер.
