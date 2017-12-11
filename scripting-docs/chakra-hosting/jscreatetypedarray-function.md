---
title: "Функция JsCreateTypedArray | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df33d0e1aadec9d7ed5aebf743e2c2f840e51fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatetypedarray-function"></a>Функция JsCreateTypedArray
Создает объект типизированного массива JavaScript.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `arrayType`  
 Тип создаваемого массива.  
  
 `baseArray`  
 Базовый массив нового массива. Используйте `JS_INVALID_REFERENCE`, если базового массива нет.  
  
 `byteOffset`  
 Смещение в байтах от начала `baseArray` (`ArrayBuffer`) для результирующего типизированного массива до ссылки. Применяется только в случае, если `baseArray` — объект `ArrayBuffer`. В противном случае — 0.  
  
 `elementLength`  
 Количество элементов в массиве. Применяется только при создании нового типизированного массива без `baseArray` (`baseArray` — это `JS_INVALID_REFERENCE`) или если `baseArray` — объект `ArrayBuffer`. В противном случае — 0.  
  
 `result`  
 Новый объект типизированного массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 `baseArray` может быть `ArrayBuffer`, другим типизированным массивом или JavaScript `Array`. Возвращаемый типизированный массив будет использовать `baseArray`, если это `ArrayBuffer`, а в противном случае будет создавать и использовать копию базового исходного массива.  
  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)