---
title: IDebugPortEvents2::Event | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9f1394e09cc6b7b695d1d19dee1f46df09f8514
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Этот метод отправляет события, которые обозначают созданием и удалением процессов и программ на порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```csharp  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pMachine`  
 [in] [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) объект, представляющий сервер отладки (один для каждого экземпляра [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]), в котором произошло событие.  
  
 `pPort`  
 [in] [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) объект, который представляет порт, в котором произошло событие.  
  
 `pProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) объект, который представляет собой процесс, в котором произошло событие.  
  
 `pProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу, в которой произошло событие.  
  
 `pEvent`  
 [in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) объекта, которое идентифицирует событие. Ниже приведены возможные события.  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 [in] Идентификатор GUID события. Поскольку события, приводится к [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) перед вызовом этого метода, этот идентификатор становится проще определить, какое событие отправляется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)