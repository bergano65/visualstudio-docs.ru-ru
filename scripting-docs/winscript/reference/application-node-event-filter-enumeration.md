---
title: "Перечисление APPLICATION_NODE_EVENT_FILTER | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "APPLICATION_NODE_EVENT_FILTER — константы"
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Перечисление APPLICATION_NODE_EVENT_FILTER
Определяет типы узлов, чтобы исключить фильтрацию документов кода.  Используемый в [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) и [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Эти константы реализованы PDM v10.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {  
    FILTER_EXCLUDE_NOTHING = 0,  
    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,  
    FILTER_EXCLUDE_EVAL_CODE = 0x2  
} APPLICATION_NODE_EVENT_FILTER;  
  
```  
  
## Члены  
  
|Элемент|Значение|Описание|  
|-------------|--------------|--------------|  
|FILTER\_EXCLUDE\_NOTHING|0x00000000|Отправьте все события.|  
|FILTER\_EXCLUDE\_ANONYMOUS\_CODE|0x00000001|Исключите анонимные узлы кода.  Эти узлы используются средой выполнения JScript для `new Function([args,] <code>)'`.|  
|FILTER\_EXCLUDE\_EVAL\_CODE|0x00000002|Исключите eval узлы кода.  Эти узлы используются средой выполнения JScript для поддержки eval.|  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)