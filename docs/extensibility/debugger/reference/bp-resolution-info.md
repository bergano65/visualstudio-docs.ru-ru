---
title: "BP_RESOLUTION_INFO | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_RESOLUTION_INFO
helpviewer_keywords: BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a08dcb196ff90343faa4b44edbb01a01e401df13
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="bpresolutioninfo"></a>BP_RESOLUTION_INFO
Описывает связанная точка останова сведения о коде точки останова или точки останова по данным.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _BP_RESOLUTION_INFO {   
   BPRESI_FIELDS          dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
} BP_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
};  
```  
  
## <a name="members"></a>Члены  
 `dwFields`  
 Коллекция флагов из [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) перечисления, указывающее, какие поля заполнены.  
  
 `bpResLocation`  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) структура, которая задает расположение точки останова в коде или в данных.  
  
 `pProgram`  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий приложение, в котором произошла ошибка точки останова.  
  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором выполняется приложение, которое содержит ошибку точки останова.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)