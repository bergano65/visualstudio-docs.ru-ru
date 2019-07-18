---
title: Перечисление JsDebugReadMemoryFlags | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c908fdbf17b13b84355dff208b7f3106bfc72087
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830466"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Перечисление JsDebugReadMemoryFlags
Флаги для задания поведения при чтении памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="values"></a>Значения  
  
|name|Описание|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Указывает, что вызывающий объект хочет, чтобы операции чтения для успешного выполнения, если только на часть памяти чтение успешно выполнена. Если задано значение, ошибка E_JsDEBUG_INVALID_MEMORY_ADDRESS будет возникать только если «Address» является недопустимым. Если этот флаг снят, ошибка E_JsDEBUG_INVALID_MEMORY_ADDRESS возникнет, если любая часть запрашиваемой памяти не удается прочитать.|  
|`None`|Указывает, что вызывающий объект хочет, чтобы поведение по умолчанию для ReadMemory.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)