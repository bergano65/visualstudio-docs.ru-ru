---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 103cefa8573c8f44efff0b53b0c09a5ec26706e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
Следующие шаги показывают простую конфигурацию служб IIS. См. Дополнительные сведения или установить на компьютер Windows Desktop, [публикация в службах IIS](https://docs.microsoft.com/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) или [IIS 8.0 с помощью ASP.NET 3.5 и ASP.NET 4.5](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Для операционных систем Windows Server, используйте **Добавить роли и компоненты** мастера через **управление** ссылку или **мониторинга** ссылку в **диспетчера серверов**. На этапе **Роли сервера** установите флажок **Веб-сервер (IIS)**.

![Роль "Веб-сервер (IIS)" выбрана на странице "Выбор ролей сервера".](../media/remotedbg-server-roles-ws2012.png)

На этапе **Службы роли** выберите нужные службы роли IIS или оставьте службы по умолчанию.

Пройдите подтверждения действия по установке роли веб-сервера и служб. После установки роли "Веб-сервер (IIS)" перезагружать сервер или перезапускать службы IIS не требуется.