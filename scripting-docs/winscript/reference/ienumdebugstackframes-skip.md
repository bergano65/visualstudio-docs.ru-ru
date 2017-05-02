---
title: "IEnumDebugStackFrames::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Skip"
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Skip
Пропустить указанное количество сегментов в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] количество сегментов в последовательности перечисления, которые нужно пропустить.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод пропустить указанное количество сегментов в последовательности перечисления.  
  
## См. также  
 [Интерфейс IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)