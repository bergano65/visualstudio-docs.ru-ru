---
title: "IEnumDebugStackFrames::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Next"
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Next
Извлекает заданное количество сегментов в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число сегментов, который необходимо извлечь.  
  
 `prgdsfd`  
 \[out\] возвращает массив интерфейсов `DebugStackFrameDescriptor`, представляющий восстанавливаемая сегменты.  
  
 `pceltFetched`  
 \[out\] фактическое количество сегментов выбирается перечислителем.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод извлекает заданное количество сегментов в последовательности перечисления.  
  
## См. также  
 [Интерфейс IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [Структура DebugStackFrameDescriptor](../../winscript/reference/debugstackframedescriptor-structure.md)