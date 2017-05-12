---
title: "Определение типа (Typedef) JsMemoryAllocationCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Определение типа (Typedef) JsMemoryAllocationCallback
Процедура обратного вызова, реализованная пользователем для событий выделения памяти.  
  
## Синтаксис  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### Параметры  
 callbackState  
 Состояние, переданное в JsSetRuntimeMemoryAllocationCallback.  
  
 allocationEvent  
 Тип события выделения типа.  
  
 allocationSize  
 Размер выделения.  
  
## Значение свойства, возвращаемое значение  
 Для события JsMemoryAllocate event возврат значения "true" позволяет среде выполнения продолжать выделение.  Возврат значения "false" показывает, что запрос выделения отклонен.  Возвращаемое значение игнорируется другими событиями выделения.  
  
## Заметки  
 Используйте JsSetRuntimeMemoryAllocationCallback для регистрации этого обратного вызова.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)