---
title: IDebugEngine2::CreatePendingBreakpoint | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a0813e077d8bdc2ba024dc932a6cb571b1b2fed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107781"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Создает ожидающая точка останова в модуль отладки (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pBPRequest`  
 [in] [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) , описывающий ожидающая точка останова для создания.  
  
 `ppPendingBP`  
 [out] Возвращает [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , представляющий ожидающая точка останова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Как правило, возвращает `E_FAIL` Если `pBPRequest` параметр не соответствует любой язык, поддерживаемый DE, если `pBPRequest` параметр неверные или неполные.  
  
## <a name="remarks"></a>Примечания  
 Ожидающая точка останова — по существу это совокупность все сведения, необходимые для привязки точки останова в коде. Ожидающая точка останова, возвращаемый этим методом, не привязан к кода до [привязки](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) вызывается метод.  
  
 Для каждого ожидающих точек останова наборы пользователей, диспетчера сеанса отладки (SDM) этот метод вызывается в каждой вложенного DE. Именно DE, чтобы проверить, точка останова является допустимым для программы, работающие в этом DE.  
  
 Когда пользователь устанавливает точку останова на строке кода, DE может выполнять привязку точки останова на ближайшую строку в документе, который соответствует этот код. Это позволяет пользователю задать точку останова на первой строке многострочного оператора, но привязать его в последней строке (где весь код помечается в отладочной информации).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простой `CProgram` объекта. Реализация DE `IDebugEngine2::CreatePendingBreakpoint` может затем пересылать все вызовы этой реализации метода в каждой программе.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)