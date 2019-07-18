---
title: 'Ошибка: Не удалось инициировать связь DCOM на удаленном компьютере | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
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
ms.openlocfilehash: 7ceb796b3a4b3cbc2b239a09ac8c173e746f194c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850909"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Ошибка: Не удалось инициировать связь DCOM на удаленном компьютере
При попытке удаленного компьютера связаться с локальным компьютером возникла ошибка DCOM. Локальный компьютер — это компьютер, на котором

 выполняется Visual Studio. Эта ошибка может возникать по нескольким причинам:

- На локальном компьютере включен брандмауэр.

- Не работает проверка подлинности Windows при обращении с удаленного компьютера на локальный.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Если локальный компьютер включен брандмауэр Windows, см. в разделе [удаленной отладки](../debugger/remote-debugging.md) инструкции о том, как настроить брандмауэр для локальной отладки.

2. Удостоверьтесь в работоспособности проверки подлинности Windows, попытавшись открыть на локальном компьютере общую папку с удаленного сервера.

3. Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.

## <a name="see-also"></a>См. также
 [Remote Debugging](../debugger/remote-debugging.md)