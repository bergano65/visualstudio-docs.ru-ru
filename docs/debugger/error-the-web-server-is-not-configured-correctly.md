---
title: 'Ошибка: Веб-сервер настроен правильно | Документы Microsoft'
ms.custom: ''
ms.date: 09/20/2017
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bf614f44ec4fedd0579f3c352e3046fa0c46e9c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Ошибка: неправильно настроен веб-сервер

После перевода этапы, описанные здесь, чтобы устранить проблему и перед повторной попыткой для отладки также может потребоваться выполнить сброс служб IIS. Это можно сделать, открыв командную строку администратора и введя `iisreset`.

Выполните следующие действия для устранения этой проблемы:

1. Если веб-приложения, размещенного на сервере настроен как сборку выпуска повторно опубликовать как отладочную сборку и убедитесь, что файл web.config содержит `debug=true` в элементе компиляции. Сброс служб IIS и повторите попытку.

    Например при использовании профиля публикации для сборки выпуска, измените его на отладки и повторной публикации. В противном случае атрибут debug будет присвоено `false` при публикации.

2. (IIS) Проверьте правильность физический путь. В службах IIS, найти этот параметр в **основные параметры > физический путь** (или **Дополнительные параметры** в предыдущих версиях IIS).

    Физический путь может быть неправильным, если веб-приложение было скопировано на другой компьютер, переименовано вручную или перемещено. Сброс служб IIS и повторите попытку.

3. При локальной отладке в Visual Studio, убедитесь, что в свойствах выбран правильный сервер. (Откройте **свойства > Web > серверов** или **свойства > Отладка** в зависимости от типа проекта. Проект Web Forms, откройте **страницы свойств > Параметры запуска > Server**).

    При использовании внешнего сервера (пользовательский), такими как службы IIS, URL-адреса должна быть правильной. В противном случае выберите IIS Express и повторите попытку.

4. (IIS) Убедитесь, что на сервере установлена необходимая версия ASP.NET.

    Несовпадение версий ASP.NET в IIS и в проекте Visual Studio может вызвать эту проблему. Необходимо установить версию платформы в файле web.config. Чтобы установить ASP.NET в IIS, используйте [установщика веб-платформы (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Кроме того, в разделе [IIS 8.0 с помощью ASP.NET 3.5 и ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) или ASP.NET Core [узла в Windows с помощью IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
4. Если `maxConnection` предел в службах IIS слишком мал и иметь слишком много подключений, может потребоваться [увеличить лимит подключений](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).
  
## <a name="see-also"></a>См. также  
 [Удаленная отладка ASP.NET на IIS на удаленном компьютере](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)