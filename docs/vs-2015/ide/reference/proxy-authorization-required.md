---
title: Требуется проверка подлинности на прокси-сервере | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2650dadddefe3be18a4406eb4fd07c5599622212
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259219"
---
# <a name="proxy-authorization-required"></a>Требуется проверка подлинности на прокси-сервере
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Эта ошибка обычно происходит, если пользователи подключаются к Visual Studio Online через прокси-сервер, который блокирует вызовы. Visual Studio Online позволяет пользователям автоматически входить в интегрированную среду разработки.  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Перезапустите Visual Studio. Должно появиться диалоговое окно проверки подлинности прокси. Введите в диалоговом окне свои учетные данные.  
  
-   Если приведенное выше действие не помогло решить проблему, возможно, прокси-сервер не запрашивает учетные данные для адресов http://go.microsoft.com, но запрашивает для адресов *.visualStudio.com. Для таких серверов необходимо включить в список разрешенных перечисленные ниже адреса, чтобы разблокировать все сценарии входа в Visual Studio.  
  
    -   *.windows.net  
  
    -   *.microsoftonline.com  
  
    -   *.visualstudio.com  
  
    -   *.microsoft.com  
  
    -   *.live.com  
  
-   В противном случае можно удалить http://go.microsoft.com адрес из списка разрешенных, чтобы диалоговое окно проверки подлинности прокси открывалось для обоих http://go.microsoft.com адрес и конечные точки сервера при запуске Visual Studio.  
  
-   OR  
  
-   Если вы хотите использовать учетные данные по умолчанию для прокси-сервера, выполните указанные ниже действия.  
  
    1.  Найдите файл devenv.exe.config (файл конфигурации devenv.exe) в папке **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (или **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).  
  
    2.  В файле конфигурации найдите блок `<system.net>` и добавьте следующий код:  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         В `proxyaddress="<http://<yourproxy:port#>`необходимо вставить правильный адрес прокси-сервера в сети.  
  
-   OR  
  
-   Добавить код, который позволит вам использовать прокси-сервер, также можно по инструкциям, приведенным в [этой публикации](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) .



