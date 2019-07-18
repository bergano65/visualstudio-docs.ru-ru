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
ms.openlocfilehash: 1112ec72e8aca764f749a6d8f1925302f569b17e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850079"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Ошибка: Не удалось инициировать подключение DCOM
При попытке локального компьютера связаться с удаленным компьютером возникла ошибка DCOM. Она вызвана либо брандмауэром на удаленном сервере, либо ошибкой проверки подлинности Windows на удаленном компьютере.

### <a name="to-correct-this-error"></a>Исправление ошибки

- Если удаленный компьютер включен брандмауэр Windows, см. в разделе [удаленной отладки](../debugger/remote-debugging.md) инструкции о том, как настроить брандмауэр для локальной отладки.

- Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)