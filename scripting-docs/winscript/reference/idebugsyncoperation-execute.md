---
title: "IDebugSyncOperation::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.Execute
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::Execute"
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::Execute
Синхронно выполняет операцию и возвращает значение.  
  
## Синтаксис  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### Параметры  
 `ppunkResult`  
 \[out\] параметр объектов, возвращенных операцией.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_ABORT`|Операция была прервана, вызвав метод `IDebugSyncOperation::InProgressAbort`.|  
  
## Заметки  
 Диспетчер процесса отладки в потоке целевого объекта вызывает метод `Execute` одновременно.  
  
## См. также  
 [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)