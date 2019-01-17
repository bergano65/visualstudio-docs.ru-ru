---
title: Перечисление JsDebugReadMemoryFlags | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bef1f16ebcf678452f2fe4b0df3ade6350120f05
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094033"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Перечисление JsDebugReadMemoryFlags
Флаги для задания поведения при чтении памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="values"></a>Значения  
  
|Имя|Описание|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Указывает, что вызывающий объект хочет, чтобы операции чтения для успешного выполнения, если только на часть памяти чтение успешно выполнена. Если задано значение, ошибка E_JsDEBUG_INVALID_MEMORY_ADDRESS будет возникать только если «Address» является недопустимым. Если этот флаг снят, ошибка E_JsDEBUG_INVALID_MEMORY_ADDRESS возникнет, если любая часть запрашиваемой памяти не удается прочитать.|  
|`None`|Указывает, что вызывающий объект хочет, чтобы поведение по умолчанию для ReadMemory.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)