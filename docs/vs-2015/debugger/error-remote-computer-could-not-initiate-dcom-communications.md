---
title: 'Ошибка: не удалось инициировать связь DCOM на удаленном компьютере | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8ddec2bdec09da1f1175b59c94db31841a1453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697341"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Ошибка: Не удалось инициировать связь DCOM на удаленном компьютере
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При попытке удаленного компьютера связаться с локальным компьютером возникла ошибка DCOM. Локальный компьютер — это компьютер, на котором  
  
 выполняется Visual Studio. Эта ошибка может возникать по нескольким причинам:  
  
- На локальном компьютере включен брандмауэр.  
  
- Не работает проверка подлинности Windows при обращении с удаленного компьютера на локальный.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Если на локальном компьютере включен брандмауэр Windows, см. инструкции по настройке брандмауэра для локальной отладки в разделе [настройка удаленные средства на устройстве](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) .  
  
2. Удостоверьтесь в работоспособности проверки подлинности Windows, попытавшись открыть на локальном компьютере общую папку с удаленного сервера.  
  
3. Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.  
  
## <a name="see-also"></a>См. также:  
 [Настройка инструментов удаленной отладки в устройстве](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
