---
title: "IRemoteDebugApplicationEvents::OnEnterBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnEnterBreakPoint
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnEnterBreakPoint"
ms.assetid: e92a56a3-c462-4a76-8ae8-4b2e6836a711
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnEnterBreakPoint
Обрабатывает событие вставки точки останова.  
  
## Синтаксис  
  
```  
HRESULT OnEnterBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### Параметры  
 `prdat`  
 \[in\] поток приложения, который ввел точку останова.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод обрабатывает событие вставки точки останова.  
  
## См. также  
 [Интерфейс IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)