---
title: "Метод IJsDebugBreakPoint::Disable | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.Disable
apilocation: jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugBreakPoint::Disable
Отключает точку останова.  
  
## Синтаксис  
  
```  
HRESULT Disable(void);  
```  
  
## Возвращаемое значение  
  
## Заметки  
 Возвращает E\_UNEXPECTED, если вызван на удаленной точке останова.  Возвращает S\_FALSE, если вызван на уже отключенной точке останова.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)