---
title: "IEnumDebugApplicationNodes::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Next
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Next"
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Next
Извлекает заданное количество сегментов в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число сегментов, который необходимо извлечь.  
  
 `pprddp`  
 \[out\] возвращает массив интерфейсов `IDebugApplicationNode`, представляющий восстанавливаемая сегменты.  
  
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
 [Интерфейс IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)