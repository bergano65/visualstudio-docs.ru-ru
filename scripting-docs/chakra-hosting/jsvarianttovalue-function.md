---
title: "Функция JsVariantToValue | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsVariantToValue
helpviewer_keywords:
- JsVariantToValue function
ms.assetid: e8f9eb8b-55b3-4b65-927e-cad5b482edee
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc778d87aab7e80e7c1b04a68c2d3b9c6fdd885a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsvarianttovalue-function"></a>Функция JsVariantToValue
Создает значение JavaScript, которое является проекцией переданного значения `VARIANT`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsVariantToValue(  
   _In_ VARIANT *variant,  
   _Out_ JsValueRef *value  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `variant`  
 Проецируемое значение `VARIANT`.  
  
 `value`  
 Значение JavaScript, которое является проекцией значения `VARIANT`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Проецируемое значение может использоваться скриптом для вызова из скрипта COM-объекта автоматизации. Хосты отвечают за реализацию правил потока COM.  
  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)