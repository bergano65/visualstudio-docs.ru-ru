---
title: "JsProjectionCallbackContext Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsProjectionCallbackContext Typedef
Контекст, передаваемый в обратный вызов приложения \(JsProjectionEnqueueCallback\) из JsRT, а затем передаваемый приложением обратно в JsRT в предоставленном обратном вызове \(`JsProjectionCallback`\) в правильном потоке.  
  
## Синтаксис  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## Заметки  
 Требует вызова `JsSetProjectionEnqueueCallback` для получения обратных вызовов.  
  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)