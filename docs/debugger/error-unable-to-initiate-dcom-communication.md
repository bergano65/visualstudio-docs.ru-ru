---
title: 'Ошибка: невозможно инициировать связь DCOM | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: ccd8b30fcba11d89e11227861c4582ff67f3a7e7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460030"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Ошибка: Не удалось инициировать подключение DCOM
При попытке локального компьютера связаться с удаленным компьютером возникла ошибка DCOM. Она вызвана либо брандмауэром на удаленном сервере, либо ошибкой проверки подлинности Windows на удаленном компьютере.

### <a name="to-correct-this-error"></a>Исправление ошибки

- Если на удаленном компьютере включен брандмауэр Windows, см. инструкции по настройке брандмауэра для локальной отладки в статье [Удаленная отладка](../debugger/remote-debugging.md).

- Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)