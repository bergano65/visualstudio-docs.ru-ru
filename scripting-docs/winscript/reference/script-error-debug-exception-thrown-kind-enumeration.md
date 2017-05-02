---
title: "Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Задает вид создаваемого исключения.  Это перечисление используется методом [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md).  
  
> [!IMPORTANT]
>  Эти константы реализованы в PDM версии 11.0 или более поздней.  Обнаружено в activdbg100.h.  
  
## Синтаксис  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## Члены  
  
|Член|Значение|Описание|  
|----------|--------------|--------------|  
|ETK\_FIRST\_CHANCE|0x00000000|Исключение является первичным.|  
|ETK\_USER\_UNHANDLED|0x00000001|Исключение не обработано в коде пользователя.|  
|ETK\_UNHANDLED|0x00000002|Исключение не обработано в коде.|  
  
## См. также  
 [IActiveScriptErrorDebug110 — интерфейс](../../winscript/reference/iactivescripterrordebug110-interface.md)