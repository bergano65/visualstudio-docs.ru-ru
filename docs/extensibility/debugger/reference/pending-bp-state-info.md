---
title: "PENDING_BP_STATE_INFO | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PENDING_BP_STATE_INFO
helpviewer_keywords: PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 909385cbf2b5fceb8d55ebe24aba763ccdf7e98a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
Содержит сведения о состоянии точки останова, можно привязать расположение кода.  
  
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
  
## <a name="members"></a>Члены  
 состояние  
 Значение из [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) перечисления, указывающее состояние ожидающая точка останова.  
  
 флаги  
 Сочетание флагов из [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) перечисления, которое указывает, виртуализируется ли точка останова.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) метод, где он заполняется.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)