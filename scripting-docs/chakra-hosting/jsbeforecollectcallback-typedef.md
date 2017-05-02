---
title: "Определение типа (Typedef) JsBeforeCollectCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58bece47-4e6d-49e7-a93d-b6a8f9928b41
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Определение типа (Typedef) JsBeforeCollectCallback
Обратный вызов, используемый перед коллекцией.  
  
## Синтаксис  
  
```  
typedef void (CALLBACK *JsBeforeCollectCallback)(  
_In_opt_ void *callbackState  
);  
```  
  
#### Параметры  
 callbackState  
 Состояние, переданное в JsSetBeforeCollectCallback.  
  
## Заметки  
 Используйте JsSetBeforeCollectCallback для регистрации этого обратного вызова.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)