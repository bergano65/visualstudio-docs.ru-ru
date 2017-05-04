---
title: "Метод IJsDebugFrame::GetDocumentPositionWithName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugFrame::GetDocumentPositionWithName
Возвращает текущее положение этого кадра стека в пределах пользовательского документа.  
  
## Синтаксис  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### Параметры  
 `pDocumentName`  
 \[out\] Для статических скриптов URL\-адрес документа.  В случае динамических скриптов возвращается имя, содержащее тип скрипта \(например, код eval, код функции и т. п\).  
  
 `pLine`  
 \[out\] Отсчитываемое от 1 положение строки в документе.  
  
 `pColumn`  
 \[out\] Отсчитываемое от 1 положение строки в документе.  
  
## Возвращаемое значение  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)