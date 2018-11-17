---
title: 'Ошибка: Убедитесь, что DNS правильно настроены на целевом компьютере | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1258b0667009d8d6ad9aafe839a76b3a838f1bcc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751055"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Ошибка: убедитесь в правильности настройки службы DNS на целевом компьютере
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При выполнении удаленной отладки может появиться следующее сообщение об ошибке:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Эта ошибка возникает, когда целевой компьютер не может определить имя главного компьютера отладчика Visual Studio. Проверьте параметры DNS на целевом компьютере.  
  
- Сведения о просмотре параметров DNS в Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 или Windows Server 2008 R2, это сделать: на **запустить** меню, выберите **Справка и поддержка** , а затем найдите **изменение параметров TCP/IP**.  
  
- Дополнительные сведения см. в статье [веб-сайта Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) и выполните поиск **изменение параметров TCP/IP**.  
  
  Если устранить неполадки DNS не удается, можно попробовать запустить удаленный отладчик с другой учетной записью. Эта ошибка возникает только при запуске удаленного отладчика с учетной записью локальной системы (Local System) или сетевой службы (Network Service) Если запустить удаленный отладчик с другой учетной записью, то для него может использоваться проверка подлинности NTLM, которая не требует использования DNS. . Для процедуры, см. в разделе [ошибка: службе удаленного отладчика Visual Studio на целевом компьютере не удается подключиться к этому компьютеру](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).



