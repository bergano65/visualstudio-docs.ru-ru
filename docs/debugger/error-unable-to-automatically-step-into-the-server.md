---
title: 'Ошибка: не удается автоматически выполнить шаг с заходом на сервер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34b298b299bb4911bfe64b362d94c3e90ecfa585
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736877"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Ошибка: не удалось автоматически перейти в режим пошагового выполнения
Текст сообщения об ошибке.

 "Не удается автоматически выполнить шаг на сервере. Отладчик не получил уведомления перед выполнением удаленной процедуры."

 Эта ошибка может возникнуть, когда предпринята попытка в пошаговом режиме зайти в веб-службу (см. раздел [Вход в пошаговом режиме в веб-службу XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Ошибка может произойти всякий раз при неправильно настроенном [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

 Возможные причины:

- Параметр отладки не установлен в "true" в файле web.config приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (см. раздел [Режим отладки в приложениях ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Версия [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] была установлена после установки Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] следует устанавливать до Visual Studio. Чтобы устранить эту неполадку, откройте **Панель управления > Windows и воспользуйтесь компонентом > Программы и компоненты** для исправления установки Visual Studio.

## <a name="see-also"></a>См. также
- [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)