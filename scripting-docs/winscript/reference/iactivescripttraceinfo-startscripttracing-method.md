---
title: "Метод IActiveScriptTraceInfo::StartScriptTracing | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод IActiveScriptTraceInfo::StartScriptTracing
Запускает трассировку скрипта.  
  
## Синтаксис  
  
```  
HRESULT StartScriptTracing(   
    [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,   
    [in] GUID guidContextID   
);  
  
```  
  
#### Параметры  
 `pSiteTraceInfo`  
 Указатель на IActiveScriptSiteTraceInfo основного приложения.  
  
 `guidContextId`  
 Идентификаторы GUID контекста.  
  
## Возвращаемое значение  
 Возможные возвращаемые значения этого метода следующие:  
  
1.  S\_ОК. Успех.  
  
2.  E\_POINTER. `pSiteTraceInfo` указатель NULL.  
  
3.  E\_NOTIMPL: Не реализуется.