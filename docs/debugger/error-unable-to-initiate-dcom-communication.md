---
title: 'Ошибка: Не удается инициировать связь DCOM | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5581a1d98b24b53aae0da674719c594de51a7bb7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Ошибка: не удалось инициировать подключение DCOM
При попытке локального компьютера связаться с удаленным компьютером возникла ошибка DCOM. Она вызвана либо брандмауэром на удаленном сервере, либо ошибкой проверки подлинности Windows на удаленном компьютере.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Если удаленный компьютер был включен брандмауэр Windows, см. раздел [удаленной отладки](../debugger/remote-debugging.md) инструкции по настройке брандмауэра для локальной отладки.  
  
-   Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.  
  
## <a name="see-also"></a>См. также  
 [Удаленная отладка](../debugger/remote-debugging.md)