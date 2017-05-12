---
title: "Функция JsStringToPointer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStringToPointer"
helpviewer_keywords: 
  - "JsStringToPointer - функция"
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsStringToPointer
Извлекает указатель на строку, относящийся к строковому значению.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### Параметры  
 `value`  
 Строковое значение, которое необходимо преобразовать в указатель на строку.  
  
 `stringValue`  
 Указатель на строку.  
  
 `stringLength`  
 Длина строки.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Эта функция извлекает указатель на строку, относящийся к строковому значению.  Она завершится сбоем с аргументом `JsErrorInvalidArgument`, если тип значения — не строка.  Возвращенное время существования строки совпадать со временем существования значения, из которого оно появилось, однако указатель на строку не считается ссылкой на значение \(и поэтому это не воспрепятствует его сбору\).  
  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)