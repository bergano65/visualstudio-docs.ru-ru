---
title: "Метод IJsDebugBreakPoint::IsEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugBreakPoint::IsEnabled
Указывает, включена ли точка останова.  
  
## Синтаксис  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### Параметры  
 `pIsEnabled`  
 \[out\] Возвращает значение true, если точка останова включена. В противном случае возвращает значение false.  
  
## Возвращаемое значение  
  
## Заметки  
 Возвращает E\_UNEXPECTED, если вызван на удаленной точке останова.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)