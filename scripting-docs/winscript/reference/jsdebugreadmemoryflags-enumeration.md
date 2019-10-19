---
title: Перечисление Жсдебугреадмеморифлагс | Документация Майкрософт
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
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571698"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Перечисление JsDebugReadMemoryFlags
Флаги для задания поведения при чтении памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="values"></a>Значения  
  
|Название|Описание|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Указывает, что вызывающему объекту требуется успешная операция чтения, если только часть памяти была прочитана. Если задано значение, то ошибка E_JsDEBUG_INVALID_MEMORY_ADDRESS будет возникать только в том случае, если адрес недопустим. Если этот флаг снят, возникнет ошибка E_JsDEBUG_INVALID_MEMORY_ADDRESS, если какая-либо часть запрошенной памяти была нечитаемой.|  
|`None`|Указывает, что вызывающему объекту требуется поведение по умолчанию для ReadMemory.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)