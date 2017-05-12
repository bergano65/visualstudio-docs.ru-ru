---
title: "IDebugStackFrame::GetDescriptionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetDescriptionString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetDescriptionString"
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetDescriptionString
Возвращает короткое или подробное текстовое описание кадра стека.  
  
## Синтаксис  
  
```  
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### Параметры  
 `fLong`  
 \[in\] пометьте, где `TRUE` возвращает длинное описание и `FALSE` возвращает краткое описание.  
  
 `pbstrDescription`  
 \[out\] описание кадра стека.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Как правило, если `fLong``FALSE`, то этот метод предоставляет только имя функции, связанной с кадром стека.  При `fLong``TRUE`, этот метод может также предоставить параметры функций и другие необходимые сведения.  
  
## См. также  
 [Интерфейс IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)