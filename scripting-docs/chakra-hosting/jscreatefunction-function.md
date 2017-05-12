---
title: "Функция JsCreateFunction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateFunction"
helpviewer_keywords: 
  - "JsCreateFunction - функция"
ms.assetid: b298a96a-5ef7-4203-a8c8-55f9bfc6d2bb
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Функция JsCreateFunction
Создает новую функцию JavaScript.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsCreateFunction(  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### Параметры  
 `nativeFunction`  
 Метод, который требуется вызвать при вызове функции.  
  
 `callbackState`  
 Предоставляемое пользователем состояние, которое будет передано обратно методу обратного вызова.  
  
 `function`  
 Новый объект функции.  
  
## Возвращаемое значение  
 Результат вызова \(если есть\).  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)