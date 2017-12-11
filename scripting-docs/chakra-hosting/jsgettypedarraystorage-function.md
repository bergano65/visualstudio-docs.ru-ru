---
title: "Функция JsGetTypedArrayStorage | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b6f4dc99c219c2ebba631c42493bc194148b497
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsgettypedarraystorage-function"></a>Функция JsGetTypedArrayStorage
Получает базовое хранилище памяти, используемое типизированным массивом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `typedArray`  
 Экземпляр типизированного массива.  
  
 `buffer`  
 Буфер массива. Время жизни возвращаемого буфера совпадает с временем жизни массива. Указатель буфера не учитывается как ссылка на массив с целью сборки мусора.  
  
 `bufferLength`  
 Количество байтов в буфере.  
  
 `arrayType`  
 Тип массива.  
  
 `elementSize`  
 Размер элемента массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)