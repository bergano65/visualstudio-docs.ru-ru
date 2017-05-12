---
title: "IDebugApplicationThreadEvents110 — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThreadEvents110 — интерфейс"
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThreadEvents110 — интерфейс
Добавить несколько событий потока.  Эти события только локально.  То есть можно подписаться на них только в процессе, отлаживанными, используя [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) advise и методы unadvise в приложении PDM поток объектов \(объекты, реализующие [Интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)\).  Они встречаются в потоке, они поступают из.  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Методы  
 Интерфейс `IDebugActivationThreadEvents110` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Вызов в поток с помощью передачи потока PDM началось|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Поток возобновляет от точки останова и будет активен еще раз.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Поток приостанавливается для точки останова и может обрабатывать вызовы, которые требуют поток полностью приостанавливается.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Вызов в поток с помощью передачи потока PDM завершен.|