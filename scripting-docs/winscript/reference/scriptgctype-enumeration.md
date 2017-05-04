---
title: "Перечисление SCRIPTGCTYPE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Перечисление SCRIPTGCTYPE
Тип сборки мусора.  Используется в методе [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md).  
  
## Синтаксис  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {  
    SCRIPTGCTYPE_NORMAL           = 0,  
    SCRIPTGCTYPE_EXHAUSTIVE       = 1,  
} SCRIPTGCTYPE;  
  
```  
  
## Значения перечисления  
  
|||  
|-|-|  
|SCRIPTGCTYPE\_NORMAL|Сделайте обычную сборки мусора.  Целое число 0.|  
|SCRIPTGCTYPE\_EXHAUSTIVE|Сделайте исчерпывающую сборки мусора.  Целое число 1.|  
  
## См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)