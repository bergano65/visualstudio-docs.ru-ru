---
title: 'Ошибка: Не удалось инициировать связь DCOM на удаленном компьютере | Документация Майкрософт'
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
ms.openlocfilehash: a1be63ddbb7b040e7efe5ce5ee6876c4bf77cb36
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990865"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Ошибка: Не удалось инициировать связь DCOM на удаленном компьютере
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При попытке удаленного компьютера связаться с локальным компьютером возникла ошибка DCOM. Локальный компьютер — это компьютер, на котором  
  
 выполняется Visual Studio. Эта ошибка может возникать по нескольким причинам:  
  
-   На локальном компьютере включен брандмауэр.  
  
-   Не работает проверка подлинности Windows при обращении с удаленного компьютера на локальный.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Если локальный компьютер включен брандмауэр Windows, см. в разделе [задать удаленных инструментов на устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) инструкции о том, как настроить брандмауэр для локальной отладки.  
  
2.  Удостоверьтесь в работоспособности проверки подлинности Windows, попытавшись открыть на локальном компьютере общую папку с удаленного сервера.  
  
3.  Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.  
  
## <a name="see-also"></a>См. также  
 [Настройка инструментов удаленной отладки в устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
