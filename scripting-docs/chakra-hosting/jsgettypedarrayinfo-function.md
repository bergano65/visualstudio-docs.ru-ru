---
title: "Функция JsGetTypedArrayInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 992bc4e9-3d06-4ad2-8b6b-88a437360f81
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция JsGetTypedArrayInfo
Получает часто используемые свойства типизированного массива.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayInfo(  
  _In_ JsValueRef typedArray,  
  _Out_opt_ JsTypedArrayType *arrayType,  
  _Out_opt_ JsValueRef *arrayBuffer,  
  _Out_opt_ unsigned int *byteOffset,  
  _Out_opt_ unsigned int *byteLength  
);  
  
```  
  
#### Параметры  
 `typedArray`  
 Экземпляр типизированного массива.  
  
 `arrayType`  
 Тип массива.  
  
 `arrayBuffer`  
 Резервное хранилище `ArrayBuffer` массива.  
  
 `byteOffset`  
 Смещение в байтах от начала буфера arrayBuffer, на который ссылается массив.  
  
 `byteLength`  
 Число байтов в массиве.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)