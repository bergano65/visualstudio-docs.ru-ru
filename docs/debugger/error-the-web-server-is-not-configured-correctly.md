---
title: 'Ошибка: Веб-сервер настроен правильно | Документация Майкрософт'
ms.date: 09/20/2017
ms.topic: troubleshooting
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
ms.openlocfilehash: 2606304ba68530c7ec893dae9cbb4954cae33112
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887494"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Ошибка: Веб-сервер настроен неправильно

После выполнения действия, описанные здесь, чтобы устранить проблему и перед повторной попыткой для отладки также может потребоваться сброс IIS. Это можно сделать, открыв командную строку администратора и введя `iisreset`.

Выполните следующие действия для устранения этой проблемы:

1. Если веб-приложение, размещенное на сервере настроен как сборку выпуска, повторная публикация как отладочную сборку и убедитесь, что файл web.config содержит `debug=true` в элементе compilation. Сброс IIS и повторите попытку.

    К примеру Если вы используете профиль публикации для выпускаемой сборки, измените его на отладки и повторной публикации. В противном случае атрибут debug будет присвоено `false` при публикации.

2. (IIS) Проверьте правильность физический путь. В IIS, можно найти этот параметр в **основные параметры > физический путь** (или **Дополнительные параметры** в предыдущих версиях IIS).

    Физический путь могут оказаться неправильными, если веб-приложение было скопировать на другой компьютер, переименовано вручную или перемещено. Сброс IIS и повторите попытку.

3. При локальной отладке в Visual Studio, убедитесь, что в окне свойств выбран правильный сервер. (Откройте **свойства > Web > серверы** или **свойства > Отладка** в зависимости от типа проекта. Для проекта веб-форм, откройте **страницы свойств > Параметры запуска > Server**).

    Если вы используете внешний сервер (пользовательский) например, IIS, URL-адреса должны быть правильными. В противном случае выберите IIS Express и повторите попытку.

4. (IIS) Убедитесь, что на сервере установлена необходимая версия ASP.NET.

    Несовпадение версий ASP.NET в IIS и в своем проекте Visual Studio может вызвать эту проблему. Может потребоваться задать версию платформы в файле web.config. Чтобы установить ASP.NET на IIS, используйте [установщика веб-платформы (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Кроме того, см. в разделе [IIS 8.0 с ASP.NET 3.5 и ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) или для ASP.NET Core, [узла в Windows со службами IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
4. Если `maxConnection` ограничение в службах IIS, слишком низкое и у вас слишком много подключений, может потребоваться [увеличить лимит подключений](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).
  
## <a name="see-also"></a>См. также раздел  
 [Удаленная отладка ASP.NET на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)