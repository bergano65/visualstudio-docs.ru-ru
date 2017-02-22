---
title: "IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
helpviewer_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает ожидается точка останова в обработчике отладки \(DE\).  
  
## Синтаксис  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```c#  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### Параметры  
 `pBPRequest`  
 \[in\] [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) объект, описывающий завершения отложенной точку останова для создания.  
  
 `ppPendingBP`  
 \[out\] возвращает IDebugPendingBreakpoint2 объект, представляющий завершения отложенной точку останова.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Обычно возвращает `E_FAIL` если  `pBPRequest` параметр не соответствует языку, поддерживаемый DE  `pBPRequest` параметр является недопустимым или незакончен.  
  
## Заметки  
 Ожидается точка останова по существу коллекция всех данных, необходимых для связывания точки останова в коде.  Ожидается точка останова, возвращаемая из этого метода не привязана к коду до [Привязка](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) вызывается метод.  
  
 Для каждой, ожидающих точки останова наборы пользователя, сеанс отладки вызовы диспетчера \(SDM\) этот метод в каждом вложенном DE.  Он до DE, чтобы убедиться, что точка останова является допустимой для программ, выполняемых в этом DE.  
  
 Если пользователь задает точку останова на строке кода, DE свободно привязки точка останова до самой ближайшей линии в документе, который соответствует этому коду.  Это делает возможным для пользователя установить точку останова на первой линии многополосной выписки, но выполняется его привязка последней линии \(где весь код приписан в данных отладки\).  
  
## Пример  
 В следующем примере показано, как реализовать этот метод для простого `CProgram` объект.  Реализация DE  `IDebugEngine2::CreatePendingBreakpoint` затем удается переадресовать все вызовы этой реализации метода содержится в каждой программе.  
  
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
  
## См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Привязка](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)