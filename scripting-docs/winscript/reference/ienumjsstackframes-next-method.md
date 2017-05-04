---
title: "Метод IEnumJsStackFrames::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IEnumJsStackFrames::Next
Получает указанное количество кадров.  
  
## Синтаксис  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### Параметры  
 `cFrameCount`  
 \[in\] Количество кадров для получения.  
  
 `pFrames`  
 \[out\] Массив для хранения кадров.  
  
 `pcFetched`  
 \[out\] Количество возвращаемых кадров.  
  
## Возвращаемое значение  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IEnumJsStackFrames](../../winscript/reference/ienumjsstackframes-interface.md)