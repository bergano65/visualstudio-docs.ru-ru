---
title: "JsPromiseContinuationCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsPromiseContinuationCallback Typedef
Обратный вызов перспективного продолжения.  
  
## Синтаксис  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Параметры  
 `task`  
  `callbackState`  
  
## Заметки  
 Узел может указать обратный вызов перспективного продолжения в `JsSetPromiseContinuationCallback`. Если скрипт создает задачу, которая должна быть выполнена позже, то будет вызван обратный вызов перспективного продолжения с задачей, а задача должна быть помещена в очередь FIFO и выполнена после завершения текущего скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)