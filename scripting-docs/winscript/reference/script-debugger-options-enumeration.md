---
title: "SCRIPT_DEBUGGER_OPTIONS — перечисление | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SCRIPT_DEBUGGER_OPTIONS — перечисление"
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPT_DEBUGGER_OPTIONS — перечисление
Указывает набор параметров и\/или возможностей, которые применяются к вложенному отладчику.  Используемый в [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) и [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Эти константы реализованы PDM v10.0 и большим.  Обнаружен в activdbg100.h.  
  
## Синтаксис  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## Члены  
  
|Элемент|Значение|Описание|  
|-------------|--------------|--------------|  
|SDO\_NONE|0x00000000|Параметры не заданы.|  
|SDO\_ENABLE\_FIRST\_CHANCE\_EXCEPTIONS|0x00000001|Указывает, что среда выполнения скриптов должна вызывать события BREAKREASON\_ERROR при возникновении исключения.  Этот параметр может быть установлен отладчиком или набором пользователь\- кодом с помощью `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO\_ENABLE\_WEB\_WORKER\_SUPPORT|0x00000002|Указывает, что вложенный отладчик поддерживает рабочих Интернета.|  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)