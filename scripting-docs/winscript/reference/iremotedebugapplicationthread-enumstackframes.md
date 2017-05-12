---
title: "IRemoteDebugApplicationThread::EnumStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.EnumStackFrames
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::EnumStackFrames"
ms.assetid: 605ce83d-43d2-47ea-b066-ec8f0da50ca6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::EnumStackFrames
Возвращает перечислитель для кадров стека, связанных с данным потоком.  
  
## Синтаксис  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Параметры  
 `ppedsf`  
 \[out\] перечислитель для кадров стека, связанных с данным потоком.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод должен вызываться из точки останова.  Перечислитель кадра стека должен возвращать кадры начальный в верхней части стека, начиная с последнего отправлянным кадром.  
  
## См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)