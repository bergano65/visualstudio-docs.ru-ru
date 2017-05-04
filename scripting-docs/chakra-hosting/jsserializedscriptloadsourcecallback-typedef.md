---
title: "JsSerializedScriptLoadSourceCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptLoadSourceCallback Typedef
Вызывается средой выполнения, чтобы загрузить исходный код сериализованного скрипта. Вызывающий объект должен сохранять буфер скрипта действительным до `JsSerializedScriptUnloadCallback`.  
  
## Синтаксис  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### Параметры  
 `sourceContext`  
 Контекст, передаваемый в `JsParseSerializedScriptWithCallback` или `JsRunSerializedScriptWithCallback`.  
  
 `scriptBuffer`  
 Возвращенный скрипт.  
  
## Заметки  
  
> [!WARNING]
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)