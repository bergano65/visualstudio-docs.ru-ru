---
title: "Требуется проверка подлинности на прокси-сервере | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Требуется проверка подлинности на прокси-сервере
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Эта ошибка обычно происходит, если пользователи подключаются к Visual Studio Online через прокси\-сервер, который блокирует вызовы. Visual Studio Online позволяет пользователям автоматически входить в интегрированную среду разработки.  
  
## Исправление ошибки  
  
-   Перезапустите Visual Studio. Должно появиться диалоговое окно проверки подлинности прокси. Введите в диалоговом окне свои учетные данные.  
  
-   Если приведенное выше действие не помогло решить проблему, возможно, прокси\-сервер не запрашивает учетные данные для адресов http:\/\/go.microsoft.com, но делает это для адресов \*.visualStudio.com. Для таких серверов необходимо включить в список разрешенных перечисленные ниже адреса, чтобы разблокировать все сценарии входа в Visual Studio.  
  
    -   \*.windows.net  
  
    -   \*.microsoftonline.com  
  
    -   \*.visualstudio.com  
  
    -   \*.microsoft.com  
  
    -   \*.live.com  
  
-   В противном случае из списка разрешенных можно удалить адрес http:\/\/go.microsoft.com, чтобы при запуске Visual Studio диалоговое окно проверки подлинности прокси\-сервера открывалось для адреса http:\/\/go.microsoft.com и конечных точек сервера.  
  
-   ИЛИ  
  
-   Если вы хотите использовать учетные данные по умолчанию для прокси\-сервера, выполните указанные ниже действия.  
  
    1.  Найдите файл devenv.exe.config \(файл конфигурации devenv.exe\) в папке **%ProgramFiles%\\Microsoft Visual Studio 14.0\\Common7\\IDE** \(или **%ProgramFiles\(x86\)%\\Microsoft Visual Studio 14.0\\Common7\\IDE**\).  
  
    2.  В файле конфигурации найдите блок `<system.net>` и добавьте следующий код:  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         В `proxyaddress="<http://<yourproxy:port#>` необходимо вставить правильный адрес прокси\-сервера в сети.  
  
-   ИЛИ  
  
-   Добавить код, который позволит вам использовать прокси\-сервер, также можно по инструкциям, приведенным в [этой публикации](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx).