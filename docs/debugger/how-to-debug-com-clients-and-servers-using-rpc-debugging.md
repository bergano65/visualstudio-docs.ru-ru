---
title: 'Как: отладка COM-клиенты и серверы с помощью отладки RPC | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4fe212015b381a38ed1cf110189b6e4839fdf9f1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Практическое руководство. Отладка клиентов и серверов COM с помощью отладки RPC
Для отладки клиент-серверных приложений COM можно использовать отладку удаленного вызова процедур (RPC). Для этого необходимо включить отладку RPC. Если отладка RPC включена, то при заходе в вызов сервера со стороны клиента отладчик подключается к серверу, позволяя выполнить отладку кода. Когда отладчик подключен, все его функции можно использовать для отладки процессов как на стороне сервера, так и на стороне клиента.  
  
### <a name="to-enable-rpc-debugging"></a>Включение отладки RPC  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  В **параметры** диалоговое окно, нажмите кнопку **Отладка** папки.  
  
3.  Нажмите кнопку **собственного** страницы.  
  
4.  Выберите **отладки RPC** флажок.  
  
    > [!NOTE]
    >  Для отладки вызовов RPC необходимо иметь привилегии администратора или опытного пользователя.  
  
    > [!NOTE]
    >  Выполнение удаленных вызовов процедур с заходом на удаленный сервер под управлением Microsoft Windows Vista будет работать только в том случае, если к удаленному серверу подключен отладчик машинного кода. В противном случае вызов RPC завершится сбоем без сообщения об ошибке. Или же вызов RPC будет выполнен, но пошаговое выполнение вызова RPC не будет работать.  
  
## <a name="see-also"></a>См. также  
 [Отладка сервера и контейнеров COM](../debugger/com-server-and-container-debugging.md)  
 [Отладка в Visual Studio](../debugger/index.md) [отладчика Обзор возможностей](../debugger/debugger-feature-tour.md)