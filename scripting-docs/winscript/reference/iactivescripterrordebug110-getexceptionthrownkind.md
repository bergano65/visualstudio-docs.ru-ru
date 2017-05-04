---
title: "IActiveScriptErrorDebug110::GetExceptionThrownKind | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110::QueryIsFirstChance"
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptErrorDebug110::GetExceptionThrownKind
Возвращает значение, показывающее вид созданного исключения.  
  
> [!IMPORTANT]
>  [IActiveScriptErrorDebug110 — интерфейс](../../winscript/reference/iactivescripterrordebug110-interface.md) реализуется в PDM версии 11.0 и более поздней.  Обнаружено в activdbg100.h.  
  
## Синтаксис  
  
```  
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### Параметры  
 `pExceptionKind`  
 \[out\] Вид создаваемого исключения \(например, первичное или необработанное\), представленный значением перечисления [Перечисление SCRIPT\_ERROR\_DEBUG\_EXCEPTION\_THROWN\_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md).  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## См. также  
 [IActiveScriptErrorDebug110 — интерфейс](../../winscript/reference/iactivescripterrordebug110-interface.md)