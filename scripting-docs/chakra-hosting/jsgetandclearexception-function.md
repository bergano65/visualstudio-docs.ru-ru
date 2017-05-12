---
title: "Функция JsGetAndClearException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetAndClearException"
helpviewer_keywords: 
  - "JsGetAndClearException - функция"
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsGetAndClearException
Возвращает исключение, которое вызвало переход среды выполнения текущего контекста в состояние исключения, и сбрасывает состояние исключения для этой среды выполнения.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### Параметры  
 `exception`  
 Исключение среды выполнения текущего контекста.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Если среда выполнения текущего контекста не находится в состоянии исключения, этот API возвращает `JsErrorInvalidArgument`.  Если среда выполнения отключена, возвращается исключение, указывающее, что сценарий был завершен, однако исключение не удаляется \(исключение будет удалено, если среда выполнения включается повторно с использованием метода `JsEnableRuntimeExecution`\).  
  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)