---
title: Сообщений с кодами. | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d995a884b8d223a4415549739c9701fd72886a56
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557779"
---
# <a name="message-codes"></a>Коды сообщений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [коды сообщений](https://docs.microsoft.com/visualstudio/debugger/message-codes).  
  
Каждая строка сообщения, отображаемая в [представления сообщений](../debugger/messages-view.md) содержит «P», элемента, "элемента," или «R». Эти коды имеют следующий смысл:  
  
|Код|Значение|  
|----------|-------------|  
|С|Сообщение отправлено в очередь с **PostMessage** функции. Сведения недоступны, о конечном размещении сообщения.|  
|S|Сообщение было отправлено с **SendMessage** функции. Это означает, что отправитель не получает управление, пока получатель обрабатывает и возвращает сообщение. Получатель таким образом, можно передать возвращаемое значение обратно отправителю.|  
|s|Сообщение было отправлено, но безопасности блокирует доступ к возвращаемому значению.|  
|К|Для каждого из них "строка имеет соответствующую строку «R» (результат), перечисляющую возвращаемое значение сообщения. Иногда вызовы сообщений являются вложенными, это означает, что этот обработчик одно сообщение отправляет другое сообщение.|



