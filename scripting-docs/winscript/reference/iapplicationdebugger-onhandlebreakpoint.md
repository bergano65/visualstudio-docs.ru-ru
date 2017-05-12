---
title: "IApplicationDebugger::onHandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onHandleBreakPoint
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onHandleBreakPoint"
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onHandleBreakPoint
Обрабатывает событие точки останова.  
  
## Синтаксис  
  
```  
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### Параметры  
 `prpt`  
 \[in\] поток, где точка останова.  
  
 `br`  
 \[in\] причина точки останова.  
  
 `pError`  
 \[in\] сведения об ошибках времени выполнения, при условии, если значение `br` BREAKREASON\_ERROR.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод вызывается после точки останова ударена и `IDebugApplication::HandleBreakPoint` Позвонитьо.  
  
 Приложение остается приостановленным, пока среда разработки отладчика не вызывает `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)