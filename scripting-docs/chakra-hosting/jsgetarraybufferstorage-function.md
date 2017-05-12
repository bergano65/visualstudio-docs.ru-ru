---
title: "Функция JsGetArrayBufferStorage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 712ae298-36a9-47ef-b089-e51835c056bc
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Функция JsGetArrayBufferStorage
Получает базовое хранилище памяти, которое использует `ArrayBuffer`.  
  
## Синтаксис  
  
```  
JsErrorCode STDAPI_ JsGetArrayBufferStorage(  
   _In_ JsValueRef arrayBuffer,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### Параметры  
 `arrayBuffer`  
 Экземпляр ArrayBuffer.  
  
 `buffer`  
 Буфер ArrayBuffer.  Время жизни возвращаемого буфера совпадает с временем жизни для `ArrayBuffer`.  Указатель буфера не учитывается как ссылка на `ArrayBuffer` с целью сборки мусора.  
  
 `bufferLength`  
 Количество байтов в буфере.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)