---
title: "IDebugStackFrame::GetThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetThread"
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetThread
Возвращает поток, связанный с данным кадром стека.  
  
## Синтаксис  
  
```  
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### Параметры  
 `ppat`  
 \[out\] поток, связанный с данным кадром стека.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает поток, связанный с данным кадром стека.  
  
## См. также  
 [Интерфейс IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)