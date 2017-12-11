---
title: "Функция JsHasProperty | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsHasProperty
helpviewer_keywords: JsHasProperty function
ms.assetid: 26c94c3d-aae6-4257-8644-df63c7e714fb
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8edbd1069936152b5edddc0561f45af2ba4ce36
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jshasproperty-function"></a>Функция JsHasProperty
Определяет, имеет ли объект свойство.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsHasProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _Out_ bool *hasProperty  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `object`  
 Объект, который может содержать свойство.  
  
 `propertyId`  
 Идентификатор свойства.  
  
 `hasProperty`  
 Указывает, имеет ли объект (или прототип) свойство.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)