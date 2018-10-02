---
title: 'Ошибка: Не удалось инициировать подключение DCOM | Документация Майкрософт'
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
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8ee1e5a9a9f799a4e9d5d8a4cc3b6f5e03b504
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562503"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Ошибка: не удалось инициировать подключение DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ошибка: не удалось инициировать подключение DCOM](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-initiate-dcom-communication).  
  
При попытке локального компьютера связаться с удаленным компьютером возникла ошибка DCOM. Она вызвана либо брандмауэром на удаленном сервере, либо ошибкой проверки подлинности Windows на удаленном компьютере.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Если удаленный компьютер включен брандмауэр Windows, см. в разделе [задать удаленных инструментов на устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) инструкции о том, как настроить брандмауэр для локальной отладки.  
  
-   Чтобы восстановить работоспособность проверки подлинности Windows, попробуйте перезагрузить оба компьютера. Изучите журналы событий на локальном и удаленном компьютерах на наличие ошибок Kerberos и узнайте у администратора домена о возможных нерешенных проблемах.  
  
## <a name="see-also"></a>См. также  
 [Удаленная отладка](../debugger/remote-debugging.md)



