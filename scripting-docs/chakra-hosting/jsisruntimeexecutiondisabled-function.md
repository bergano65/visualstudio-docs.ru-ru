---
title: "Функция JsIsRuntimeExecutionDisabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsRuntimeExecutionDisabled"
helpviewer_keywords: 
  - "JsIsRuntimeExecutionDisabled - функция"
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Функция JsIsRuntimeExecutionDisabled
Возвращает значение, указывающее, отключено ли в среде выполнения выполнение скрипта.  
  
## Синтаксис  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(  
    _In_ JsRuntimeHandle runtime,  
    _Out_ bool *isDisabled  
);  
```  
  
#### Параметры  
 `runtime`  
 Задает среду выполнения, чтобы проверить, отключено ли выполнение.  
  
 `isDisabled`  
 Значение `true`, если выполнение отключено; в противном случае — значение `false`.  
  
## Возвращаемое значение  
 Значение `JsNoError`, если операция завершена успешно; в противном случае — код сбоя.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)