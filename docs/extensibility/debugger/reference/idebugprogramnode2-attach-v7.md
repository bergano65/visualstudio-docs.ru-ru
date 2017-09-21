---
title: "IDebugProgramNode2::Attach_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::Attach"
helpviewer_keywords: 
  - "IDebugProgramNode2::Attach_V7"
  - "IDebugProgramNode2::Attach"
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

НЕРЕКОМЕНДУЕМЫЙ.  НЕ ИСПОЛЬЗУЙТЕ.  
  
## Синтаксис  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```c#  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### Параметры  
 `pMDMProgram`  
 \[in\] IDebugProgram2 интерфейс, представляющий программы, чтобы вложить.  
  
 `pCallback`  
 \[in\] IDebugEventCallback2 интерфейс, используемый отправлять отладочные события в SDM.  
  
 `dwReason`  
 \[in\] значение из [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисление, указывающее причину вложить.  
  
## Возвращаемое значение  
 Реализация всегда должна возвращать `E_NOTIMPL`.  
  
## Заметки  
  
> [!WARNING]
>  От [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]этот метод больше не используется и не должен всегда возвращать  `E_NOTIMPL`.  См. [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейс для альтернативного подхода, если узел программы требуется отобразить, то нельзя вложить или если узел программы просто устанавливает программы  `GUID`. В противном случае реализация  [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  
  
## В Visual Studio 2005  
 Этому методу требуется реализовывать только если DE выполняется в адресном пространстве отлаживаемой программы.  В противном случае этот метод должен возвращать `S_FALSE`.  
  
 При вызове этого метода, должен отправлять DE [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) объект события, если он еще не был отправлен для данного экземпляра  [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) интерфейс, а также  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) и  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) объекты событий.  [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) затем отправляется, если объект события  `dwReason` параметр  `ATTACH_REASON_LAUNCH`.  
  
 DE должен вызвать метод [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) метод  [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, предоставляемый  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) объект события и должен хранить GUID этой программы в данных экземпляра  `IDebugProgram2` объект, на который DE.  
  
## См. также  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)