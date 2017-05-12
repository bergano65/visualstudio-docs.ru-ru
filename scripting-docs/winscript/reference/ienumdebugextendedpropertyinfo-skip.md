---
title: "IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Skip"
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Skip
Пропустить указанное количество структур `ExtendedDebugPropertyInfo` в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число структур `ExtendedDebugPropertyInfo` в последовательности перечисления, которые нужно пропустить.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  Возвращает `S_FALSE` и задает указатель текущего элемента в конец перечисления, если `celt` больше числа элементов в выйденных перечислитель.  
  
## См. также  
 [Интерфейс IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Структура ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)