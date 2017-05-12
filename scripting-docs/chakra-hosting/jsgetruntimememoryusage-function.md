---
title: "Функция JsGetRuntimeMemoryUsage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetRuntimeMemoryUsage"
helpviewer_keywords: 
  - "JsGetRuntimeMemoryUsage - функция"
ms.assetid: b9bd4146-bfbc-4cb1-a0e9-a0ded7fb09bd
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsGetRuntimeMemoryUsage
Получает текущее использование памяти для среды выполнения.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryUsage(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryUsage  
);  
```  
  
#### Параметры  
 `runtime`  
 Среда выполнения, использование памяти которой необходимо извлечь.  
  
 `memoryUsage`  
 Текущее использование памяти среды выполнения в байтах.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Можно всегда извлечь использование памяти независимо от того, активна ли среда выполнения в другом потоке.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)