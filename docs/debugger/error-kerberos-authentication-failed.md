---
title: 'Ошибка: Сбой проверки подлинности Kerberos | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63b3ed3349403bef0c85af9775f77cc980fc4e63
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="error-kerberos-authentication-failed"></a>Ошибка: сбой проверки подлинности Kerberos
В ходе удаленной отладки может возникнуть следующее сообщение об ошибке:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.  
```  
  
 Эта ошибка возникает, когда монитор удаленной отладки Visual Studio выполняется от имени учетной записи локальной системы (LocalSystem) или учетной записи сетевой службы (NetworkService). Работая под одной из этих учетных записей, удаленный отладчик должен установить соединение с аутентификацией на основе Kerberos, чтобы иметь возможность возвращать данные главному компьютеру отладчика Visual Studio.  
  
 Проверка подлинности Kerberos невозможна при следующих условиях:  
  
-   Удаленный компьютер или главный компьютер с отладчиком включен в рабочую группу, а не в домен.  
  
     \- или -  
  
-   Служба Kerberos на контроллере домена была отключена.  
  
 Если аутентификация на основе Kerberos недоступна, следует сменить учетную запись, от имени которой выполняется монитор удаленной отладки Visual Studio. Процедуры см. в разделе [ошибка: службе удаленного отладчика Visual Studio на целевом компьютере не удается подключиться к этому компьютеру](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
 Если оба компьютера входят в один и тот же домен, но это сообщение возникает снова, проверьте, что служба DNS на целевом компьютере правильно определяет имя главного компьютера. Выполните описанные ниже действия.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Для проверки того, что DNS на целевом компьютере правильно распознает имя главного компьютера:  
  
1.  На целевом компьютере откройте **запустить** последовательно выберите пункты **стандартные** и нажмите кнопку **командной строки**.  
  
2.  В **командной строки** привилегиями, введите:  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3.  В первой строке ответа `ping` будет выведено полное имя компьютера и IP-адрес, возвращаемый службой DNS для указанного компьютера.  
  
4.  Откройте на ведомому компьютеру отладчика, **командной строки** и выполните `ipconfig`.  
  
5.  Сравните значения IP-адресов.  
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и устранения неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)