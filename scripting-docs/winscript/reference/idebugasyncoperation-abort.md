---
title: "IDebugAsyncOperation::Abort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.Abort
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::Abort"
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::Abort
Отменяет операцию.  
  
## Синтаксис  
  
```  
HRESULT Abort();  
```  
  
#### Параметры  
 Этот метод не принимает параметры.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|S\_OK|Метод успешно выполнен.|  
|E\_NOTIMPL|Операция не может быть отменена.|  
  
## Заметки  
 Этот метод обычно вызывается из потока отладчика для отмены операции безответная.  Этот метод вызывает метод `InProgressAbort` в объекте `IDebugSyncOperation` непосредственного вызова.  
  
## См. также  
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)