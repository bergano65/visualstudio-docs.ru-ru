---
title: BP_CONDITION | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d49c912ae14154fc552c76fc011596f4f22166f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994108"
---
# <a name="bpcondition"></a>BP_CONDITION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает условия, при которых срабатывает точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий активный поток приложения, содержащего точку останова.  
  
 `styleCondition`  
 Значение из [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) перечисление, описывающее стиль этого условия точки останова.  
  
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
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
