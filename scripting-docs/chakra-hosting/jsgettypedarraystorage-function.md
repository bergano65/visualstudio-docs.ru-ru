---
title: "Функция JsGetTypedArrayStorage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Функция JsGetTypedArrayStorage
Получает базовое хранилище памяти, используемое типизированным массивом.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### Параметры  
 `typedArray`  
 Экземпляр типизированного массива.  
  
 `buffer`  
 Буфер массива.  Время жизни возвращаемого буфера совпадает с временем жизни массива.  Указатель буфера не учитывается как ссылка на массив с целью сборки мусора.  
  
 `bufferLength`  
 Количество байтов в буфере.  
  
 `arrayType`  
 Тип массива.  
  
 `elementSize`  
 Размер элемента массива.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)