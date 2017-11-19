---
title: "Ошибка: Удаленный компьютер не удалось инициировать связь DCOM | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 377211f0ca7e4095da58b169f113689db9c7b41e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Ошибка: не удалось инициировать связь DCOM на удаленном компьютере
При попытке удаленного компьютера связаться с локальным компьютером возникла ошибка DCOM. Локальный компьютер — это компьютер, на котором  
  
 выполняется Visual Studio. Эта ошибка может возникать по нескольким причинам:  
  
-   На локальном компьютере включен брандмауэр.  
  
-   Не работает проверка подлинности Windows при обращении с удаленного компьютера на локальный.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Если локальный компьютер был включен брандмауэр Windows, см. раздел [удаленной отладки](../debugger/remote-debugging.md) инструкции по настройке брандмауэра для локальной отладки.  
  
2.  Удостоверьтесь в работоспособности проверки подлинности Windows, попытавшись открыть на локальном компьютере общую папку с удаленного сервера.  
  
3.  Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.  
  
## <a name="see-also"></a>См. также  
 [Удаленная отладка](../debugger/remote-debugging.md)