---
title: "IDebugApplication::GetCurrentThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.GetCurrentThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::GetCurrentThread"
ms.assetid: 15128e77-6fc6-42a2-8c04-20e22ef03f29
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::GetCurrentThread
Возвращает поток, связанный с выполняющийся в данный момент поток.  
  
## Синтаксис  
  
```  
HRESULT GetCurrentThread(  
   IDebugApplicationThread**  pat  
);  
```  
  
#### Параметры  
 `pat`  
 \[out\] поток, связанный с выполняющийся в данный момент поток.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает поток, связанный с выполняющийся в данный момент поток.  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)