---
title: "Перечисление JsMemoryEventType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsMemoryEventType"
helpviewer_keywords: 
  - "JsMemoryEventType - перечисление"
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Перечисление JsMemoryEventType
Тип события обратного вызова выделения.  
  
## Синтаксис  
  
```  
enum JsMemoryEventType;  
```  
  
## Участники  
  
### Значения  
  
|Имя|Описание|  
|---------|--------------|  
|`JsMemoryAllocate`|Обозначает запрос на выделение памяти.|  
|`JsMemoryFailure`|Обозначает завершившееся сбоем событие выделения.|  
|`JsMemoryFree`|Обозначает событие освобождения памяти.|  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)