---
title: IDebugEventCallback2::Event | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ea52b8be040df50da1585165599c4fdea635557
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Отправляет уведомление о событиях отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pEngine`  
 [in] [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , представляющий модуль отладки (DE), который отправляет это событие. Для заполнения этого параметра требуется DE.  
  
 `pProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) объект, который представляет собой процесс, в котором происходит событие. Этот параметр будет заполнено диспетчером сеанса отладки (SDM). DE всегда передает значение null для этого параметра.  
  
 `pProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу, в котором возникает это событие. Для большинства событий этот параметр не является значение null.  
  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором возникает это событие. Для события остановки, этот параметр не может быть значение null, кадр стека, полученное из этого параметра.  
  
 `pEvent`  
 [in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , представляющий событие отладки.  
  
 `riidEvent`  
 [in] Идентификатор GUID, определяющий интерфейс событий, который нужно получить из `pEvent` параметра.  
  
 `dwAttrib`  
 [in] Сочетание флагов из [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 При вызове этого метода `dwAttrib` параметра должно соответствовать значение, возвращенное [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) переданный метод, как он вызван для объекта события `pEvent` параметра.  
  
 Все события отладки учитываются асинхронно, независимо от того, событие сам асинхронной или нет. Когда DE вызывает этот метод, возвращаемое значение не определить, было ли обработано событие, только ли событие было получено. На самом деле в большинстве случаев это событие не была обработана при возвращении этим методом.  
  
## <a name="see-also"></a>См. также  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)