---
title: 'Ошибка: Удаленный компьютер не удалось инициировать связь DCOM | Документация Майкрософт'
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
ms.openlocfilehash: 9e936292010c73decffadc5b215156f2200ed8b3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683078"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Ошибка: не удалось инициировать связь DCOM на удаленном компьютере
При попытке удаленного компьютера связаться с локальным компьютером возникла ошибка DCOM. Локальный компьютер — это компьютер, на котором

 выполняется Visual Studio. Эта ошибка может возникать по нескольким причинам:

-   На локальном компьютере включен брандмауэр.

-   Не работает проверка подлинности Windows при обращении с удаленного компьютера на локальный.

### <a name="to-correct-this-error"></a>Исправление ошибки

1.  Если локальный компьютер включен брандмауэр Windows, см. в разделе [удаленной отладки](../debugger/remote-debugging.md) инструкции о том, как настроить брандмауэр для локальной отладки.

2.  Удостоверьтесь в работоспособности проверки подлинности Windows, попытавшись открыть на локальном компьютере общую папку с удаленного сервера.

3.  Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.

## <a name="see-also"></a>См. также раздел
 [Remote Debugging](../debugger/remote-debugging.md)