---
title: "Ошибка: убедитесь в правильности настройки службы DNS на целевом компьютере | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.callback_dns_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка: убедитесь в правильности настройки службы DNS на целевом компьютере
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При выполнении удаленной отладки может появиться следующее сообщение об ошибке:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Эта ошибка возникает, когда целевой компьютер не может определить имя главного компьютера отладчика Visual Studio.  Проверьте параметры DNS на целевом компьютере.  
  
-   Для получения дополнительных сведений о просмотре параметров DNS в Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 или Windows Server 2008 R2 выполните следующие действия: в меню **Пуск** выберите пункт **Справка и поддержка**, а затем выполните поиск по ключевым словам "изменение параметров TCP\/IP".  
  
-   Для получения дополнительных сведений посетите [веб\-сайт Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) и выполните поиск по ключевым словам "изменение параметров TCP\/IP".  
  
 Если устранить неполадки DNS не удается, можно попробовать запустить удаленный отладчик с другой учетной записью.  Эта ошибка возникает только при запуске удаленного отладчика с учетной записью локальной системы \(Local System\) или сетевой службы \(Network Service\)  Если запустить удаленный отладчик с другой учетной записью, то для него может использоваться проверка подлинности NTLM, которая не требует использования DNS.  .  Инструкции см. в разделе [Ошибка: службе удаленного отладчика Visual Studio не удается подключиться к этому компьютеру](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).