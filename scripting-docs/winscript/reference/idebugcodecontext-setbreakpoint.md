---
title: "IDebugCodeContext::SetBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.SetBreakPoint
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::SetBreakPoint"
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::SetBreakPoint
Задает или снимите клиринги точку останова в этом контексте кода.  
  
## Синтаксис  
  
```  
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### Параметры  
 `bps`  
 \[in\] определяет состояние точки останова для этого контекста кода.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод устанавливает или снимает точку останова в этом контексте кода.  
  
## См. также  
 [Интерфейс IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)   
 [Перечисление BREAKPOINT\_STATE](../../winscript/reference/breakpoint-state-enumeration.md)