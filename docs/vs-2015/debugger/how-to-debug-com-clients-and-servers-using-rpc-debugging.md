---
title: 'Практическое: отладка COM-клиентов и серверов, с помощью отладки RPC | Документация Майкрософт'
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
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b64c01f502dbe4194561776f121e21475d61d43
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560689"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Практическое руководство. Отладка клиентов и серверов COM с помощью отладки RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: отладка COM-клиенты и серверы с помощью отладки RPC](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-com-clients-and-servers-using-rpc-debugging).  
  
Для отладки клиент-серверных приложений COM можно использовать отладку удаленного вызова процедур (RPC). Для этого необходимо включить отладку RPC. Если отладка RPC включена, то при заходе в вызов сервера со стороны клиента отладчик подключается к серверу, позволяя выполнить отладку кода. Когда отладчик подключен, все его функции можно использовать для отладки процессов как на стороне сервера, так и на стороне клиента.  
  
### <a name="to-enable-rpc-debugging"></a>Включение отладки RPC  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  В **параметры** диалоговом окне щелкните **Отладка** папки.  
  
3.  Нажмите кнопку **собственного** страницы.  
  
4.  Выберите **отладки RPC** "флажок".  
  
    > [!NOTE]
    >  Для отладки вызовов RPC необходимо иметь привилегии администратора или опытного пользователя.  
  
    > [!NOTE]
    >  Выполнение удаленных вызовов процедур с заходом на удаленный сервер под управлением Microsoft Windows Vista будет работать только в том случае, если к удаленному серверу подключен отладчик машинного кода. В противном случае вызов RPC завершится сбоем без сообщения об ошибке. Или же вызов RPC будет выполнен, но пошаговое выполнение вызова RPC не будет работать.  
  
## <a name="see-also"></a>См. также  
 [Отладка COM-сервера и контейнеров](../debugger/com-server-and-container-debugging.md)   
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)



