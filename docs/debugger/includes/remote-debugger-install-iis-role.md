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
ms.openlocfilehash: dbc9d727dc412e3d354d806a45c352eef810cd99
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
Следующие шаги показывают простую конфигурацию служб IIS. См. Дополнительные сведения или установить на компьютер Windows Desktop, [публикация в службах IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) или [IIS 8.0 с помощью ASP.NET 3.5 и ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Для операционных систем Windows Server, используйте **Добавить роли и компоненты** мастера через **управление** ссылку или **мониторинга** ссылку в **диспетчера серверов**. На этапе **Роли сервера** установите флажок **Веб-сервер (IIS)**.

![Роль "Веб-сервер (IIS)" выбрана на странице "Выбор ролей сервера".](../media/remotedbg-server-roles-ws2012.png)

На этапе **Службы роли** выберите нужные службы роли IIS или оставьте службы по умолчанию.

Пройдите подтверждения действия по установке роли веб-сервера и служб. После установки роли "Веб-сервер (IIS)" перезагружать сервер или перезапускать службы IIS не требуется.