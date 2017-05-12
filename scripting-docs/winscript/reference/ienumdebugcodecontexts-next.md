---
title: "IEnumDebugCodeContexts::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Next"
ms.assetid: 844cc353-ae0b-45e1-84a6-32b0bb67f57f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Next
Извлекает заданное количество сегментов в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число сегментов, который необходимо извлечь.  
  
 `pscc`  
 \[out\] возвращает массив интерфейсов `IDebugCodeContext`, представляющий восстанавливаемая сегменты.  
  
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
 [Интерфейс IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)