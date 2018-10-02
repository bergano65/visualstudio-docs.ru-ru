---
title: IDebugBoundBreakpoint2::GetHitCount | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb87f8bb1b737da35ddd7734b698623efcb3ea86
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561926"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugBoundBreakpoint2::GetHitCount](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount).  
  
Возвращает текущий счетчик числа попаданий для данная связанная точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetHitCount(   
   DWORD* pdwHitCount  
);  
```  
  
```csharp  
int GetHitCount(   
   out uint pdwHitCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwHitCount`  
 [out] Возвращает число попаданий.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` Если состояние объекта связанная точка останова присваивается `BPS_DELETED` (частью [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисления).  
  
## <a name="remarks"></a>Примечания  
 Число попаданий — количество раз, когда данная точка останова возникло во время выполнения текущего сеанса.  
  
## <a name="see-also"></a>См. также  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)

