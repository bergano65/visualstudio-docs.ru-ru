---
title: PENDING_BP_STATE_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cea960e35b0ff56720f8c687fafdea1fe8e6a6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991389"
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
Содержит сведения о состоянии точки останова, которая готова для привязки к расположение кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```csharp  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## <a name="members"></a>Участники  
 состояние  
 Значение из [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) перечисление, указывающее состояние ожидающая точка останова.  
  
 флаги  
 Сочетание флагов из [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) перечисление, указывающее, виртуализируется ли точка останова.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) метод, где он заполняется.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)