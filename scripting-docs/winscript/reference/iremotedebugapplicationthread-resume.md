---
title: "IRemoteDebugApplicationThread::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.Resume
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::Resume"
ms.assetid: ac290861-515d-4f06-b452-3b96f54e538c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::Resume
Возобновляется поток.  
  
## Синтаксис  
  
```  
HRESULT Resume(  
   DWORD*  pdwCount  
);  
```  
  
#### Параметры  
 `pdwCount`  
 \[out\] количество приостановка потока.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Когда этот метод возобновляет поток, он уменьшает счетчик приостановки.  
  
## См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)