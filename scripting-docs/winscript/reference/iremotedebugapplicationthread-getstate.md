---
title: "IRemoteDebugApplicationThread::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetState"
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetState
Возвращает состояние данного потока.  
  
## Синтаксис  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### Параметры  
 `pState`  
 \[out\] сочетание следующих национальные флаги потока:  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|THREAD\_STATE\_RUNNING|0x00000001|Поток выполняется.|  
|THREAD\_STATE\_SUSPENDED|0x00000002|Поток приостановлен.|  
|THREAD\_BLOCKED|0x00000004|Поток заблокирован.|  
|THREAD\_OUT\_OF\_CONTEXT|0x00000008|Поток из содержимого.|  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает состояние данного потока.  
  
## См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)