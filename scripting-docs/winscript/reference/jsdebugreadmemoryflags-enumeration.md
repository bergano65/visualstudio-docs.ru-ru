---
title: "Перечисление JsDebugReadMemoryFlags | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7efb5170bf0314e95b1acded39a897c2236a29ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Перечисление JsDebugReadMemoryFlags
Флаги для задания поведения при чтении памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="values"></a>Значения  
  
|Имя|Описание|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Указывает, что вызывающий объект хочет, чтобы операции чтения для успешного выполнения, если только часть памяти, чтение успешно выполнено. Если это значение задано, E_JsDEBUG_INVALID_MEMORY_ADDRESS ошибка будет возникать только если «Адрес» является недопустимым. Если этот флажок снят, E_JsDEBUG_INVALID_MEMORY_ADDRESS возникает ошибка, если не удается прочитать любой части запрошенный объем памяти.|  
|`None`|Указывает, что вызывающий объект хочет, чтобы поведение по умолчанию для ReadMemory.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)