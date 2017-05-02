---
title: "Перечисление SCRIPTTRACEINFO | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Перечисление SCRIPTTRACEINFO
Представляет событие скрипта, трассируется.  Используемый в [Метод IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## Синтаксис  
  
```  
typedef enum tagSCRIPTTRACEINFO {    
    SCRIPTTRACEINFO_SCRIPTSTART = 0,    
    SCRIPTTRACEINFO_SCRIPTEND   = 1,    
    SCRIPTTRACEINFO_COMCALLSTART    = 2,    
    SCRIPTTRACEINFO_COMCALLEND  = 3,    
    SCRIPTTRACEINFO_CREATEOBJSTART  = 4,    
    SCRIPTTRACEINFO_CREATEOBJEND    = 5,    
    SCRIPTTRACEINFO_GETOBJSTART = 6,    
    SCRIPTTRACEINFO_GETOBJEND   = 7,    
} SCRIPTTRACEINFO ;  
```  
  
## Значения перечисления  
  
|||  
|-|-|  
|SCRIPTTRACEINFO\_SCRIPTSTART|Запуск сценария.|  
|SCRIPTTRACEINFO\_SCRIPTEND|Конец сценария.|  
|SCRIPTTRACEINFO\_COMCALLSTART|Начало вызова COM.|  
|SCRIPTTRACEINFO\_COMCALLEND|Завершение вызова COM.|  
|SCRIPTTRACEINFO\_CREATEOBJSTART|Начало создания объекта.|  
|SCRIPTTRACEINFO\_CREATEOBJEND|Завершение создания объекта.|  
|SCRIPTTRACEINFO\_GETOBJSTART|Начало вызова GetObject.|  
|SCRIPTTRACEINFO\_GETOBJEND|Завершение вызова GetObject.|