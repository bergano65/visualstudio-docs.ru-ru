---
title: "Функция JsGetNullValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetNullValue"
helpviewer_keywords: 
  - "JsGetNullValue - функция"
ms.assetid: 132a1496-8dfe-4d3c-a8f8-389f5b0b50d2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsGetNullValue
Получает значение `null` в текущем контексте скрипта.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetNullValue(  
   _Out_ JsValueRef *nullValue  
);  
```  
  
#### Параметры  
 `nullValue`  
 Значение `null`.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)