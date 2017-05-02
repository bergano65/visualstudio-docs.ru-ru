---
title: "JsProjectionEnqueueCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsProjectionEnqueueCallback Typedef
Обратный вызов приложения, который вызывается средой JsRT, когда API проекции выполняется не в исходном, а в другом потоке.  
  
## Синтаксис  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Параметры  
 `jsCallback`  
 Обратный вызов, который должен вызываться в исходном потоке.  
  
 `jsContext`  
 Контекст приложений.  
  
 `callbackState`  
 Контекст JsRT, который должен быть передан в `jsCallback`.  
  
## Заметки  
 Требует вызова JsSetProjectionEnqueueCallback для получения обратных вызовов.  
  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)