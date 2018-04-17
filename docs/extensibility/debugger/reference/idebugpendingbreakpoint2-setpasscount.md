---
title: IDebugPendingBreakpoint2::SetPassCount | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21e39c54249add3b5d57cd6db907256122aab56b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Задает или изменяет количество прохода, связанные с ожидающая точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bpPassCount`  
 [in] Объект [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структуру, содержащую число проход.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_BP_DELETED` Если точка останова была удалена.  
  
## <a name="remarks"></a>Примечания  
 Теряются все проход счетчик, который был ранее связан с ожидающая точка останова. Все точки останова, привязанный из этого ожидающих точек останова, называются присваивается подсчета количества проход `bpPassCount` параметра.  
  
## <a name="see-also"></a>См. также  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)