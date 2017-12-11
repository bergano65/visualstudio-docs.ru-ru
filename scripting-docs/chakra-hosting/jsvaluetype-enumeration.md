---
title: "Перечисление JsValueType | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsValueType
helpviewer_keywords: JsValueType enumeration
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4f61cf9118c19a0fc35e7505af422b812d0b43
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsvaluetype-enumeration"></a>Перечисление JsValueType
Тип JavaScript ссылки JsValueRef.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="members"></a>Члены  
  
### <a name="values"></a>Значения  
  
|Имя|Описание|  
|----------|-----------------|  
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
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)