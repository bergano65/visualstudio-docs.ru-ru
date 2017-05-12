---
title: "Функция JsCreateExternalObject | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateExternalObject"
helpviewer_keywords: 
  - "JsCreateExternalObject - функция"
ms.assetid: 6bcef506-93fb-429b-b06a-a971ff0b71f3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsCreateExternalObject
Создает новый объект, который хранит некие внешние данные.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalObject(  
   _In_opt_ void *data,  
   _In_opt_ JsFinalizeCallback finalizeCallback,  
   _Out_ JsValueRef *object  
);  
```  
  
#### Параметры  
 `data`  
 Внешние данные, которые будет представлять объект.  Может принимать значение NULL.  
  
 `finalizeCallback`  
 Обратный вызов для времени после завершения объекта.  Может принимать значение NULL.  
  
 `object`  
 Новый объект.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)