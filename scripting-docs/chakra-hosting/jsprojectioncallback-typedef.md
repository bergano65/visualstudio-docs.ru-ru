---
title: "JsProjectionCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsProjectionCallback Typedef
Обратный вызов JsRT, который должен вызываться с контекстом, передаваемым в `JsProjectionEnqueueCallback` в правильном потоке.  
  
## Синтаксис  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### Параметры  
 `jsContext`  
 Требует вызова `JsSetProjectionEnqueueCallback` для получения обратных вызовов.  
  
## Заметки  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)