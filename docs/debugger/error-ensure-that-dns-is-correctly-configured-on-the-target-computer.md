---
title: 'Ошибка: Убедитесь, что DNS на целевом компьютере правильно настроены | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a349dc3a1e2368b4e1772d4bf717483d5bc2dc5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Ошибка: убедитесь в правильности настройки службы DNS на целевом компьютере
При выполнении удаленной отладки может появиться следующее сообщение об ошибке:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Эта ошибка возникает, когда целевой компьютер не может определить имя главного компьютера отладчика Visual Studio. Проверьте параметры DNS на целевом компьютере.  
  
-   Сведения о просмотре параметров DNS в Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 или Windows Server 2008 R2, это сделать: на **запустить** меню, выберите **Справка и поддержка** и выполните поиск **изменение параметров TCP/IP**.  
  
-   Дополнительные сведения см. в [веб-сайта Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) и выполните поиск **изменение параметров TCP/IP**.  
  
 Если устранить неполадки DNS не удается, можно попробовать запустить удаленный отладчик с другой учетной записью. Эта ошибка возникает только при запуске удаленного отладчика с учетной записью локальной системы (Local System) или сетевой службы (Network Service) Если запустить удаленный отладчик с другой учетной записью, то для него может использоваться проверка подлинности NTLM, которая не требует использования DNS. . Процедуры см. в разделе [ошибка: службе удаленного отладчика Visual Studio на целевом компьютере не удается подключиться к этому компьютеру](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).