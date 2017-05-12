---
title: "Определение типа JsSerializedScriptUnloadCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Определение типа JsSerializedScriptUnloadCallback
Вызывается средой выполнения по завершении обработки всех ресурсов, связанных с выполнением скрипта. Вызывающий объект на этом этапе должен освободить источник, если он загружен, байтовый код и контекст.  
  
## Синтаксис  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### Параметры  
 `sourceContext`  
 Контекст, передаваемый в `JsParseSerializedScriptWithCallback` или `JsRunSerializedScriptWithCallback`.  
  
## Заметки  
  
> [!WARNING]
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)