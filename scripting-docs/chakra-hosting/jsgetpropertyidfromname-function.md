---
title: "Функция JsGetPropertyIdFromName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetPropertyIdFromName"
helpviewer_keywords: 
  - "JsGetPropertyIdFromName - функция"
ms.assetid: 1674906f-746a-4c62-99cd-023276683a86
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsGetPropertyIdFromName
Получает идентификатор свойства, связанный с именем.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromName(  
   _In_z_ const wchar_t *name,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### Параметры  
 `name`  
 Имя идентификатора свойства, которое нужно получить или создать.  Имя может содержать только цифры.  
  
 `propertyId`  
 Идентификатор свойства в данной среде выполнения для указанного имени.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Идентификаторы свойств относятся к определенному контексту и не могут использоваться в любых контекстах.  
  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)