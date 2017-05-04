---
title: "Функция JsCreateExternalArrayBuffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция JsCreateExternalArrayBuffer
Создает объект `ArrayBuffer` Javascript для доступа к внешней памяти.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### Параметры  
 `data`  
 Указатель на внешнюю память.  
  
 `byteLength`  
 Количество байтов во внешней памяти.  
  
 `finalizeCallback`  
 Обратный вызов для времени после завершения объекта. Может принимать значение NULL.  
  
 `callbackState`  
 Предоставляемое пользователем состояние, которое будет передано обратно в finalizeCallback.  
  
 `result`  
 Новый объект `ArrayBuffer`.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)