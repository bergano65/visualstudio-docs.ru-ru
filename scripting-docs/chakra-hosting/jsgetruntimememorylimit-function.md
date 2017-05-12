---
title: "Функция JsGetRuntimeMemoryLimit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsGetRuntimeMemoryLimit - функция"
ms.assetid: ed81ca60-99fd-46b0-89ae-f6ac07926904
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsGetRuntimeMemoryLimit
Получает текущий лимит памяти для среды выполнения.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryLimit  
);  
```  
  
#### Параметры  
 `runtime`  
 Среда выполнения, лимит которой необходимо извлечь.  
  
 `memoryLimit`  
 Текущий лимит памяти среды выполнения в байтах или \-1, если лимит не задан.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Можно всегда извлечь лимит памяти среды выполнения независимо от того, активна ли среда выполнения в другом потоке.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)