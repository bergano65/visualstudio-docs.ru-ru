---
title: Сообщений с кодами. | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 33707cf748ff19af4780d4ded7f74ebf52d007d1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209781"
---
# <a name="message-codes"></a>Коды сообщений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Каждая строка сообщения, отображаемая в [представления сообщений](../debugger/messages-view.md) содержит «P», элемента, "элемента," или «R». Эти коды имеют следующий смысл:  
  
|Код|Значение|  
|----------|-------------|  
|С|Сообщение отправлено в очередь с **PostMessage** функции. Сведения недоступны, о конечном размещении сообщения.|  
|S|Сообщение было отправлено с **SendMessage** функции. Это означает, что отправитель не получает управление, пока получатель обрабатывает и возвращает сообщение. Получатель таким образом, можно передать возвращаемое значение обратно отправителю.|  
|s|Сообщение было отправлено, но безопасности блокирует доступ к возвращаемому значению.|  
|К|Для каждого из них "строка имеет соответствующую строку «R» (результат), перечисляющую возвращаемое значение сообщения. Иногда вызовы сообщений являются вложенными, это означает, что этот обработчик одно сообщение отправляет другое сообщение.|



