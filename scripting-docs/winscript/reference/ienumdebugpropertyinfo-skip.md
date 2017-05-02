---
title: "IEnumDebugPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Skip"
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Skip
Пропустить указанное количество структур `DebugPropertyInfo` в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число структур `DebugPropertyInfo` в последовательности перечисления, которые нужно пропустить.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  Возвращает `S_FALSE` и задает указатель текущего элемента в конец перечисления, если `celt` больше числа элементов в выйденных перечислитель.  
  
## См. также  
 [Интерфейс IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)