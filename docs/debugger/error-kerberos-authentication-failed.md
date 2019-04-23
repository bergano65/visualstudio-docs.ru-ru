---
title: 'Ошибка: Сбой проверки подлинности Kerberos | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
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
ms.openlocfilehash: 76a62a821a9b110be2ffd8e25cbdf6721f12bc08
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087570"
---
# <a name="error-kerberos-authentication-failed"></a>Ошибка: сбой проверки подлинности Kerberos
В ходе удаленной отладки может возникнуть следующее сообщение об ошибке:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 Эта ошибка возникает, когда монитор удаленной отладки Visual Studio выполняется от имени учетной записи локальной системы (LocalSystem) или учетной записи сетевой службы (NetworkService). Работая под одной из этих учетных записей, удаленный отладчик должен установить соединение с аутентификацией на основе Kerberos, чтобы иметь возможность возвращать данные главному компьютеру отладчика Visual Studio.

 Проверка подлинности Kerberos невозможна при следующих условиях:

- Удаленный компьютер или ведущий компьютер с отладчиком включен в рабочую группу, а не в домен.

   \- или -

- Служба Kerberos на контроллере домена была отключена.

  Если аутентификация на основе Kerberos недоступна, следует сменить учетную запись, от имени которой выполняется монитор удаленной отладки Visual Studio. Для процедуры, см. в разделе [ошибка: Служба удаленного отладчика Visual Studio на целевом компьютере не удается подключиться к этому компьютеру](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

  Если оба компьютера входят в один и тот же домен, но это сообщение возникает снова, проверьте, что служба DNS на целевом компьютере правильно определяет имя главного компьютера. Выполните описанные ниже действия.

### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Для проверки того, что DNS на целевом компьютере правильно распознает имя главного компьютера:

1. На целевом компьютере войдите в меню **Пуск** и выберите в меню **Стандартные** пункт **Командная строка**.

2. В окне **командной строки** введите:

    ```cmd
    ping <debugger_host_computer_name>
    ```

3. В первой строке ответа `ping` будет выведено полное имя компьютера и IP-адрес, возвращаемый службой DNS для указанного компьютера.

4. На главном компьютере откройте приложение **Командная строка** и выполните команду `ipconfig`.

5. Сравните значения IP-адресов.

## <a name="see-also"></a>См. также
- [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
