---
title: "Функция JsNumberToInt | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Функция JsNumberToInt
Извлекает значение `int` из числового значения.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### Параметры  
 `value`  
 Числовое значение для преобразования в значение `int`.  
  
 `intValue`  
 Значение `int`.  
  
## Возвращаемое значение  
  
## Заметки  
 Эта функция извлекает значение из числового значения и преобразует в значение `int`.  Она завершится сбоем с аргументом `JsErrorInvalidArgument`, если тип значения — не число.  
  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)