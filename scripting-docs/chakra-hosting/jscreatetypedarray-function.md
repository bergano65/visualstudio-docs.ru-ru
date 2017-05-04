---
title: "Функция JsCreateTypedArray | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Функция JsCreateTypedArray
Создает объект типизированного массива JavaScript.  
  
## Синтаксис  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### Параметры  
 `arrayType`  
 Тип создаваемого массива.  
  
 `baseArray`  
 Базовый массив нового массива.  Используйте `JS_INVALID_REFERENCE`, если базового массива нет.  
  
 `byteOffset`  
 Смещение в байтах от начала `baseArray` \(`ArrayBuffer`\) для результирующего типизированного массива до ссылки.  Применяется только в случае, если `baseArray` — объект `ArrayBuffer`.  В противном случае — 0.  
  
 `elementLength`  
 Количество элементов в массиве.  Применяется только при создании нового типизированного массива без `baseArray` \(`baseArray` — это `JS_INVALID_REFERENCE`\) или если `baseArray` — объект `ArrayBuffer`.  В противном случае — 0.  
  
 `result`  
 Новый объект типизированного массива.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 `baseArray` может быть `ArrayBuffer`, другим типизированным массивом или JavaScript `Array`.  Возвращаемый типизированный массив будет использовать `baseArray`, если это `ArrayBuffer`, а в противном случае будет создавать и использовать копию базового исходного массива.  
  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)