---
title: 'Ошибка: Не удалось инициировать подключение DCOM | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1dc250666c5f60064016b90121f7238f9e6e19ae
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682730"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Ошибка: не удалось инициировать подключение DCOM
При попытке локального компьютера связаться с удаленным компьютером возникла ошибка DCOM. Она вызвана либо брандмауэром на удаленном сервере, либо ошибкой проверки подлинности Windows на удаленном компьютере.

### <a name="to-correct-this-error"></a>Исправление ошибки

-   Если удаленный компьютер включен брандмауэр Windows, см. в разделе [удаленной отладки](../debugger/remote-debugging.md) инструкции о том, как настроить брандмауэр для локальной отладки.

-   Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.

## <a name="see-also"></a>См. также раздел
- [Remote Debugging](../debugger/remote-debugging.md)