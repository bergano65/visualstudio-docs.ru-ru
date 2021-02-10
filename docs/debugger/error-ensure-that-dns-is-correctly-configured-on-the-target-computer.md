---
title: убедитесь в правильности настройки службы DNS на целевом компьютере | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cc16217b20d08e9ad2d3b43d3b074652fdffec95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871686"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Ошибка: убедитесь в правильности настройки службы DNS на целевом компьютере
При выполнении удаленной отладки может появиться следующее сообщение об ошибке:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.
```

 Эта ошибка возникает, когда целевой компьютер не может определить имя главного компьютера отладчика Visual Studio. Проверьте параметры DNS на целевом компьютере.

- Для получения дополнительных сведений о просмотре параметров DNS в Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 или Windows Server 2008 R2 выполните следующие действия: в меню **Пуск** выберите пункт **Справка и поддержка**, а затем выполните поиск по ключевым словам **изменение параметров TCP/IP**.

- Для получения дополнительных сведений посетите [веб-сайт Microsoft Windows](https://www.microsoft.com/windows/) и выполните поиск по ключевым словам **изменение параметров TCP/IP**.

  Если устранить неполадки DNS не удается, можно попробовать запустить удаленный отладчик с другой учетной записью. Эта ошибка возникает только при запуске удаленного отладчика с учетной записью локальной системы (Local System) или сетевой службы (Network Service) Если запустить удаленный отладчик с другой учетной записью, то для него может использоваться проверка подлинности NTLM, которая не требует использования DNS. . Инструкции см. в статье [Ошибка: службе удаленного отладчика Visual Studio не удается подключиться к этому компьютеру](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
