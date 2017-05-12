---
title: "Перечисление JsValueType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueType"
helpviewer_keywords: 
  - "JsValueType - перечисление"
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Перечисление JsValueType
Тип JavaScript ссылки JsValueRef.  
  
## Синтаксис  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## Участники  
  
### Значения  
  
|Имя|Описание|  
|---------|--------------|  
|`JsUndefined`|Это значение представляет собой значение `undefined`.|  
|`JsNull`|Это значение представляет собой значение `null`.|  
|`JsNumber`|Это значение представляет собой числовое значение JavaScript.|  
|`JsString`|Это значение представляет собой строковое значение JavaScript.|  
|`JsBoolean`|Это значение представляет собой логическое значение JavaScript.|  
|`JsObject`|Это значение представляет собой объектное значение JavaScript.|  
|`JsFunction`|Это значение представляет собой объектное значение функции JavaScript.|  
|`JsError`|Это значение представляет собой значение объекта ошибки JavaScript.|  
|`JsArray`|Это значение представляет собой значение объекта массива JavaScript.|  
|`JsSymbol`|Это значение представляет собой символьное значение JavaScript.<br /><br /> Это значение перечисления поддерживается только в режиме Edge.|  
|`JsArrayBuffer`|Это значение представляет собой объектное значение JavaScript `ArrayBuffer`.<br /><br /> Это значение перечисления поддерживается только в режиме Edge.|  
|`JsTypedArray`|Это значение представляет собой типизированное значение объекта массива JavaScript.<br /><br /> Это значение перечисления поддерживается только в режиме Edge.|  
|`JsDataView`|Это значение представляет собой объектное значение JavaScript `DataView`.<br /><br /> Это значение перечисления поддерживается только в режиме Edge.|  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)