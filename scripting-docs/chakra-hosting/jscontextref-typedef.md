---
title: "Определение типа (Typedef) JsContextRef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Определение типа (Typedef) JsContextRef
Ссылка на контекст скрипта.  
  
## Синтаксис  
  
```  
typedef JsRef JsContextRef;  
```  
  
## Заметки  
 Каждый контекст скрипта содержит собственный глобальный объект, отличающийся от глобальных объектов других контекстов скрипта.  
  
 Многие API размещения Chakra требуют «активного» скриптового контекста, настроить который можно с помощью `JsSetCurrentContext`.  Хосты\-API Chakra, для которых необходимо задать контекст, будут обозначены в своей документации.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)