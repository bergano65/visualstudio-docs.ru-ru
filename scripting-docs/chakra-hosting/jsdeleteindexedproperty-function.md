---
title: "Функция JsDeleteIndexedProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDeleteIndexedProperty"
helpviewer_keywords: 
  - "JsDeleteIndexedProperty - функция"
ms.assetid: cc876839-2ecd-41a8-82d0-c19b3de944e3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsDeleteIndexedProperty
Удалите значение, расположенное по заданному индексу объекта.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsDeleteIndexedProperty(  
   _In_ JsValueRef object,  
   _In_ JsValueRef index  
);  
```  
  
#### Параметры  
 `object`  
 Объект для выполнения операции.  
  
 `index`  
 Удаляемый индекс.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)