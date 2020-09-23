---
title: не удалось инициировать связь DCOM на удаленном компьютере | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 92a03c89cfd1bf0e0772d1a1728ffb9b0754d089
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852593"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Ошибка: Не удалось инициировать связь DCOM на удаленном компьютере
При попытке удаленного компьютера связаться с локальным компьютером возникла ошибка DCOM. Локальный компьютер — это компьютер, на котором

 выполняется Visual Studio. Эта ошибка может возникать по нескольким причинам:

- На локальном компьютере включен брандмауэр.

- Не работает проверка подлинности Windows при обращении с удаленного компьютера на локальный.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Если на локальном компьютере включен брандмауэр Windows, см. инструкции по настройке брандмауэра для локальной отладки в статье [Удаленная отладка](../debugger/remote-debugging.md).

2. Удостоверьтесь в работоспособности проверки подлинности Windows, попытавшись открыть на локальном компьютере общую папку с удаленного сервера.

3. Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.

## <a name="see-also"></a>См. также
 [Remote Debugging](../debugger/remote-debugging.md)