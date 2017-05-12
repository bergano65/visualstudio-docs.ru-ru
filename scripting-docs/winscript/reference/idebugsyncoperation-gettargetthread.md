---
title: "IDebugSyncOperation::GetTargetThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.GetTargetThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::GetTargetThread"
ms.assetid: e6eeeb90-b5ed-4727-8434-fa3186c25013
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::GetTargetThread
Возвращает поток приложения целевого объекта для синхронной операции.  
  
## Синтаксис  
  
```  
HRESULT GetTargetThread(  
   IDebugApplicationThread**  ppatTarget  
);  
```  
  
#### Параметры  
 `ppatTarget`  
 \[out\] поток приложения целевого объекта для синхронной операции.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает поток приложения целевого объекта для синхронной операции.  
  
## См. также  
 [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)