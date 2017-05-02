---
title: "Перечисление JsDebugReadMemoryFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Перечисление JsDebugReadMemoryFlags
Флаги для задания поведения при чтении памяти.  
  
## Синтаксис  
  
```  
enum JsDebugReadMemoryFlags  
{  
   None = 0,  
   JsDebugAllowPartialRead= 0x1  
} JsDebugReadMemoryFlags;  
```  
  
## Члены  
  
### Значения  
  
|Имя|Описание|  
|---------|--------------|  
|`JsDebugAllowPartialRead`|Указывает, что вызывающий объект требует, чтобы операция чтения завершалась успешно, если только часть чтения памяти завершилась успешно.  Если он установлен, ошибка E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS возникнет, только если "Address" является недействительным.  Если этот флаг снят, ошибка E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS возникнет, если какая\-либо часть запрашиваемой памяти недоступна для чтения.|  
|`None`|Указывает, что вызывающий объект ожидает поведение по умолчанию для ReadMemory.|  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)