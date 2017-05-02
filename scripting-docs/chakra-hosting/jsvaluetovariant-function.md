---
title: "Функция JsValueToVariant | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueToVariant"
helpviewer_keywords: 
  - "JsValueToVariant - функция"
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsValueToVariant
Инициализирует переданный элемент `VARIANT` как проекцию значения JavaScript.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### Параметры  
 `object`  
 Значение JavaScript, которое необходимо проецировать как элемент `VARIANT`.  
  
 `variant`  
 Указатель на структуру `VARIANT`, которая будет инициализирована как проекция.  
  
## Возвращаемое значение  
  
## Заметки  
 Проекция `VARIANT` может использоваться клиентами автоматизации COM для вызова спроецированного объекта JavaScript.  
  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)