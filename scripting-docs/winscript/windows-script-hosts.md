---
title: "Серверы скриптов Windows | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Сервер скриптов Windows, реализация узлов"
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Серверы скриптов Windows
При реализации средства обработки сценариев Microsoft Windows можно безопасно высказывать вызывает обработчик скриптов только интерфейс [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) в контексте базового потока до тех пор, пока узел выполняются следующие действия.  
  
-   Выберите базовый поток \(обычно поток, содержащий цикл обработки сообщений\).  
  
-   Создайте обработчик скриптов в основном потоке.  
  
-   Вызывает методы обработчика скриптов только из базового потока, за исключением случаев, когда специально разрешено, как в случаях [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) и [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
-   Вызывает объект диспетчеризации обработчика скриптов только из базового потока.  
  
-   Гарантирует, что цикл обработки сообщений выполняется в основном потоке, если дескриптор окна предоставляется.  
  
-   Гарантирует, что объекты в событиях источника объектной модели узла только в основном потоке.  
  
 Эти правила автоматически следует ни с одними продетыми потоков всеми узлами.  Ограничения модели, описанной выше намеренно свободно достаточно, чтобы разрешить узел, чтобы прервать вставленный скрипт путем вызова [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) из другого потока \(начатого обработчиком CTRL\+BREAK или подобием\) или дублирования скрипт в новом потоке с помощью [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## Заметки  
 Ни один из этих ограничений, которые применяются к узлу, который выбирает реализовать состояние многопоточного интерфейс [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) и состояние продетую в объектной модели.  Такой узел может использовать интерфейс [IActiveScript](../winscript/reference/iactivescript.md) из любого потока, без ограничений.  
  
## См. также  
 [\<PAVE OVER\> Интерфейсы скриптов Microsoft Windows — введение](http://msdn.microsoft.com/library/3d10169f-2984-49ef-90c6-dd89c97f1dd6)