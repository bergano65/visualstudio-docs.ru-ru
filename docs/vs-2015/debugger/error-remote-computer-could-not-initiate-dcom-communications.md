---
title: 'Ошибка: Удаленный компьютер не удалось инициировать связь DCOM | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79548e2fbfbb4c10ce912ab90cd0541aea7f1200
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571905"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Ошибка: не удалось инициировать связь DCOM на удаленном компьютере
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ошибка: не удалось инициировать связь DCOM на удаленном компьютере](https://docs.microsoft.com/visualstudio/debugger/error-remote-computer-could-not-initiate-dcom-communications).  
  
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



