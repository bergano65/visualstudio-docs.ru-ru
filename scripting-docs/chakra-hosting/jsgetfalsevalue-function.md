---
title: "Функция JsGetFalseValue | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetFalseValue
helpviewer_keywords: JsGetFalseValue function
ms.assetid: 621a584c-4ca8-4ba0-b19a-6cb50cf830b6
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f05f6fc6852010c4728b4dae82bcf6a74ac29992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetfalsevalue-function"></a>Функция JsGetFalseValue
Получает значение `false` в текущем контексте скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetFalseValue(  
   _Out_ JsValueRef *falseValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `falseValue`  
 Значение `false`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)