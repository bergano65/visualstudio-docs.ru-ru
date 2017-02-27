---
title: "Ошибка: сбой проверки подлинности Kerberos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.callback_kerberos_auth_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c18053f9-9074-4bc3-a8bf-13e4acbea921
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Ошибка: сбой проверки подлинности Kerberos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В ходе удаленной отладки может возникнуть следующее сообщение об ошибке:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos auythentication failed.  
```  
  
 Эта ошибка возникает, когда монитор удаленной отладки Visual Studio выполняется от имени учетной записи локальной системы \(LocalSystem\) или учетной записи сетевой службы \(NetworkService\).  Работая под одной из этих учетных записей, удаленный отладчик должен установить соединение с аутентификацией на основе Kerberos, чтобы иметь возможность возвращать данные главному компьютеру отладчика Visual Studio.  
  
 Проверка подлинности Kerberos невозможна при следующих условиях:  
  
-   Удаленный компьютер или ведущий компьютер с отладчиком включен в рабочую группу, а не в домен.  
  
     \- либо \-  
  
-   Служба Kerberos на контроллере домена была отключена.  
  
 Если аутентификация на основе Kerberos недоступна, следует сменить учетную запись, от имени которой выполняется монитор удаленной отладки Visual Studio.  Инструкции см. в разделе [Ошибка: службе удаленного отладчика Visual Studio не удается подключиться к этому компьютеру](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
 Если оба компьютера входят в один и тот же домен, но это сообщение возникает снова, проверьте, что служба DNS на целевом компьютере правильно определяет имя ведущего компьютера.  Выполните описанные ниже действия.  
  
### Для проверки того, что DNS на целевом компьютере правильно распознает имя ведущего компьютера:  
  
1.  На целевом компьютере войдите в меню **Пуск** и выберите в меню **Стандартные** пункт **Командная строка**.  
  
2.  В окне **Командная строка** введите:  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3.  В первой строке ответа `ping` будет выведено полное имя компьютера и IP\-адрес, возвращаемый службой DNS для указанного компьютера.  
  
4.  На ведущем компьютере откройте приложение **Командная строка** и выполните команду `ipconfig`.  
  
5.  Сравните значения IP\-адресов.  
  
## См. также  
 [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)