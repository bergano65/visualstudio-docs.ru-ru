---
title: "Перечисление BREAKPOINT_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKPOINT_STATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKPOINT_STATE — перечисление"
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Перечисление BREAKPOINT_STATE
Отображает состояние точек останова.  
  
## Синтаксис  
  
```  
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## Члены  
  
|Элемент|Описание|  
|-------------|--------------|  
|BREAKPOINT\_DELETED|Точка останова больше не существует, но по\-прежнему ссылки на него.|  
|BREAKPOINT\_DISABLED|Точка останова существует, но запретитьа.|  
|BREAKPOINT\_ENABLED|Точка останова существует и включена.|  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)