---
title: "IDebugApplication::GetBreakFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.GetBreakFlags
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::GetBreakFlags"
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::GetBreakFlags
Возвращает текущие флаги останова для приложения.  
  
## Синтаксис  
  
```  
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### Параметры  
 `pabf`  
 \[out\] текущий break пометит для приложения.  
  
 `pprdatSteppingThread`  
 \[out\] выполняющийся в данный момент поток.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает текущие флаги останова для приложения.  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Перечисление APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)