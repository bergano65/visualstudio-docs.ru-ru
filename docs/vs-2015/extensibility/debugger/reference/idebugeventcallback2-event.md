---
title: IDebugEventCallback2::Event | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e47ce39ec9e911a0daed628736aa7ed52e73d8c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805493"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Отправляет уведомление о событиях отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) объект, представляющий процесс, в котором происходит событие. Этот параметр заполняется диспетчером сеанса отладки (SDM). DE всегда передает значение null для этого параметра.  
  
 `pProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу, в котором происходит это событие. Для большинства событий этот параметр не имеет значение null.  
  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором происходит это событие. Для события остановки, этот параметр не может иметь значение null, кадр стека при получении от этого параметра.  
  
 `pEvent`  
 [in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , представляющий событие отладки.  
  
 `riidEvent`  
 [in] Идентификатор GUID, определяющий интерфейс событий, который нужно получить из `pEvent` параметра.  
  
 `dwAttrib`  
 [in] Сочетание флагов из [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 При вызове этого метода `dwAttrib` должен соответствовать значение, возвращаемое из [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) переданный метода, вызываемого на объекте события `pEvent` параметра.  
  
 Все события отладки учитываются асинхронно, независимо от того, ли событие сам является асинхронным, или нет. При использовании DE вызывает этот метод, возвращаемое значение указывает ли событие обработано, только ли получения события. На самом деле в большинстве случаев это событие не была обработана при возвращении данного метода.  
  
## <a name="see-also"></a>См. также  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)

