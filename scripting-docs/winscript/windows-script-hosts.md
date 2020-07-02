---
title: Серверы скриптов Windows | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51053dec1f8362aa9eef80e4867d2f92a06454cb
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835333"
---
# <a name="windows-script-hosts"></a>Серверы скриптов Windows
При реализации сервера скриптов Microsoft Windows можно с уверенностью предположить, что обработчик скриптов вызывает интерфейс [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) только в контексте базового потока при условии, что узел выполняет следующие действия:  
  
- выбирает базовый поток (обычно поток, который содержит цикл обработки сообщений);  
  
- создает обработчик скриптов в базовом потоке;  
  
- вызывает методы обработчика скриптов только из базового потока, за исключением того, где специально разрешено, как в случаях [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) и [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md);  
  
- вызывает объект диспетчеризации обработчика скриптов только из базового потока;  
  
- гарантирует, что цикл обработки сообщений выполняется в базовом потоке, если указан дескриптор окна;  
  
- гарантирует, что в модели объекта узла только исходные события в базовом потоке.  
  
  Этим правилам автоматически следуют все однопотоковые узлы. Описанная выше ограниченная модель намеренно является достаточно свободной, чтобы разрешать узлу прерывать зациклившийся скрипт путем вызова [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) из другого потока (инициированного обработчиком CTRL+BREAK или аналогичным) или дублировать скрипт в новый поток с помощью [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="remarks"></a>Комментарии  
 Ни одно из этих ограничений не применяется к узлу, который выбирает реализацию свободнопоточного интерфейса [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) и свободнопоточную объектную модель. Такой узел может использовать интерфейс [IActiveScript](../winscript/reference/iactivescript.md) из любого потока без ограничений.  
  
## <a name="see-also"></a>Дополнительно  
 [Интерфейсы скриптов Windows](../winscript/windows-script-interfaces.md)