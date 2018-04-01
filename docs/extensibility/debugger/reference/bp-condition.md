---
title: BP_CONDITION | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9ccc0b142e87acd3a09840f8c72f5fe1a35bc0a4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="bpcondition"></a>BP_CONDITION
Описывает условия, при которых срабатывает точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```csharp  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## <a name="members"></a>Участники  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий активного потока для приложения, которое содержит точку останова.  
  
 `styleCondition`  
 Значение из [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) перечисление, описывающее стиль условие для точки останова.  
  
 `bstrContext`  
 Расположение точки останова.  
  
 `bstrCondition`  
 Условия срабатывания точки останова.  
  
 `nRadix`  
 Основание системы счисления для использования в оценке все числовые данные.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является членом [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
 Эта структура также передается в качестве параметра [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) и [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) методы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)