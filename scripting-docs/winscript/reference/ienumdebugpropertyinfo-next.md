---
title: "IEnumDebugPropertyInfo::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Next"
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Next
Извлекает заданное количество структур `DebugPropertyInfo` в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Next (  
   ULONG celt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число структур `DebugPropertyInfo`, который необходимо извлечь.  
  
 `rgelt`  
 \[out\] массив структур `DebugPropertyInfo` полученных.  
  
 `pceltFetched`  
 \[out\] возвращает число фактически полученных структур `DebugPropertyInfo`.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  
  
## См. также  
 [Интерфейс IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)