---
title: "Функция JsSetRuntimeMemoryAllocationCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryAllocationCallback"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryAllocationCallback - функция"
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsSetRuntimeMemoryAllocationCallback
Задает обратный вызов выделения памяти для указанной среды выполнения  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### Параметры  
 `runtime`  
 Среда выполнения, для которой необходимо зарегистрировать обратный вызов выделения.  
  
 `callbackState`  
 Предоставляемое пользователем состояние, которое будет передано обратно методу обратного вызова.  
  
 `allocationCallback`  
 Обратный вызов выделения памяти, который необходимо выполнять для событий выделения памяти.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 При регистрации обратного вызова выделения памяти среда выполнения выполняет обратный вызов хоста всякий раз, когда получает память от операционной системы или освобождает память для ОС.  Процедура обратного вызова вызывается, прежде чем диспетчер памяти среды выполнения выделяет блок памяти.  Выделение будет отклонено, если обратный вызов возвращает значение false.  Диспетчер памяти среды выполнения также вызовет процедуру обратного вызова после освобождения блока памяти, а также после ошибок выделения.  
  
 Обратный вызов выполняется в текущем потоке выполнения среды выполнения, поэтому выполнение блокируется до завершения обратного вызова.  
  
 Возвращаемое значение функции обратного вызова не сохраняется; ранее отклоненные выделения не препятствуют вызову метода обратного вызова средой выполнения в будущем для новых выделений памяти.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)