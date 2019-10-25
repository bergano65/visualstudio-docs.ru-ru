---
title: 'Ошибка: удаленному компьютеру не удалось инициировать связь DCOM | Документация Майкрософт'
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
ms.openlocfilehash: 2d61fe145a8dc301c928b81f9b57f1a574865a1d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737552"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Ошибка: не удалось инициировать связь DCOM на удаленном компьютере
При попытке удаленного компьютера связаться с локальным компьютером возникла ошибка DCOM. Локальный компьютер — это компьютер, на котором

 выполняется Visual Studio. Эта ошибка может возникать по нескольким причинам:

- На локальном компьютере включен брандмауэр.

- Не работает проверка подлинности Windows при обращении с удаленного компьютера на локальный.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Если на локальном компьютере включен брандмауэр Windows, см. инструкции по настройке брандмауэра для локальной отладки в разделе [Удаленная отладка](../debugger/remote-debugging.md) .

2. Удостоверьтесь в работоспособности проверки подлинности Windows, попытавшись открыть на локальном компьютере общую папку с удаленного сервера.

3. Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.

## <a name="see-also"></a>См. также
 [Remote Debugging](../debugger/remote-debugging.md)