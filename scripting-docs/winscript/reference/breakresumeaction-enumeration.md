---
title: "Перечисление BREAKRESUMEACTION | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKRESUMEACTION — перечисление"
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Перечисление BREAKRESUMEACTION
Описывает способы продолжения выполнения из точки останова.  
  
## Синтаксис  
  
```  
typedef enum tagBREAKRESUME_ACTION {    BREAKRESUMEACTION_ABORT,    BREAKRESUMEACTION_CONTINUE,    BREAKRESUMEACTION_STEP_INTO,    BREAKRESUMEACTION_STEP_OVER,    BREAKRESUMEACTION_STEP_OUT,    BREAKRESUMEACTION_IGNORE,    BREAKRESUMEACTION_STEP_DOCUMENT, } BREAKRESUMEACTION;  
```  
  
## Члены  
  
|Член|Описание|  
|----------|--------------|  
|BREAKRESUMEACTION\_ABORT|Прерывает приложение.|  
|BREAKRESUMEACTION\_CONTINUE|Продолжает выполнение.|  
|BREAKRESUMEACTION\_STEP\_INTO|Выполняет шаг с заходом в процедуру.|  
|BREAKRESUMEACTION\_STEP\_OVER|Выполняет шаг с обходом процедуры.|  
|BREAKRESUMEACTION\_STEP\_OUT|Выходит из текущей процедуры.|  
|BREAKRESUMEACTION\_IGNORE|Продолжает выполнение с состоянием.|  
|BREAKRESUMEACTION\_STEP\_DOCUMENT|Переходит к следующему документу.|  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)