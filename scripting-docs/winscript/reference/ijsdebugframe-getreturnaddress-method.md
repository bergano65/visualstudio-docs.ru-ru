---
title: "Метод IJsDebugFrame::GetReturnAddress | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetReturnAddress
apilocation: jscript9diag.dll
ms.assetid: 7f10c1d6-d7b9-402e-9020-04cded37f9d3
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugFrame::GetReturnAddress
Получает обратный адрес, отправленный в "начале" \(см. GetStackRange\) кадра.  
  
## Синтаксис  
  
```  
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### Параметры  
 `pReturnAddress`  
 \[out\] Обратный адрес.  
  
## Возвращаемое значение  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)