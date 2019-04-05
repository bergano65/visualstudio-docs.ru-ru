---
title: IDebugProgramNode2::Attach_V7 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c02973faf1d65ff8be79cd387666f35651db7bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992488"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

РЕКОМЕНДУЕТСЯ К ИСПОЛЬЗОВАНИЮ. НЕ ИСПОЛЬЗУЙТЕ.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pMDMProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс, который представляет присоединение к программе.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) интерфейс, который будет использоваться для отправки событий отладки SDM.  
  
 `dwReason`  
 [in] Значение из [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисления, которое указывает причину для присоединения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация всегда должны возвращать `E_NOTIMPL`.  
  
## <a name="remarks"></a>Примечания  
  
> [!WARNING]
>  Начиная с версии [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], этот метод больше не используется и всегда должны возвращать `E_NOTIMPL`. См. в разделе [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейс альтернативный подход, если узел программы должен указывать, он не может быть присоединен к или если узел программы именно просто установить программу `GUID`. В противном случае реализация [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  
  
## <a name="prior-to-visual-studio-2005"></a>До Visual Studio 2005  
 Этот метод должен быть реализован только в том случае, если выполняется DE в адресном пространстве отлаживаемой программы. В противном случае этот метод должен возвращать `S_FALSE`.  
  
 При вызове этого метода, необходимо отправить DE [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) объект события, если он уже не был отправлен для данного экземпляра [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) интерфейс, а также [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) и [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) объектов событий. [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) объект события затем отправляется, если `dwReason` параметр `ATTACH_REASON_LAUNCH`.  
  
 Необходимо вызвать DE [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) метод [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объекта, заданного параметром [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) события объекта и необходимо сохранить идентификатор GUID этой программы в данных экземпляра для `IDebugProgram2` объект, реализуемый DE.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
