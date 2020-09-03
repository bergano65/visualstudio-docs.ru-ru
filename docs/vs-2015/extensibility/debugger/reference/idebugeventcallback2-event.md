---
title: 'IDebugEventCallback2:: Event | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 37462b5f274ca6e6c2a4a2feb4083ea94ea2f066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163971"
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
 окне Объект [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , представляющий модуль отладки (de), который отправляет это событие. Для заполнения этого параметра требуется DE.  
  
 `pProcess`  
 окне Объект [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий процесс, в котором происходит событие. Этот параметр заполняется диспетчером отладки сеансов (SDM). Параметр DE всегда передает значение NULL для этого параметра.  
  
 `pProgram`  
 окне Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, в которой происходит это событие. Для большинства событий этот параметр не имеет значение null.  
  
 `pThread`  
 окне Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором происходит это событие. Для событий остановки этот параметр не может иметь значение null, так как кадр стека получается из этого параметра.  
  
 `pEvent`  
 окне Объект [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , представляющий событие отладки.  
  
 `riidEvent`  
 окне Идентификатор GUID, определяющий интерфейс события, который необходимо получить из `pEvent` параметра.  
  
 `dwAttrib`  
 окне Сочетание флагов из перечисления [евентаттрибутес](../../../extensibility/debugger/reference/eventattributes.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 При вызове этого метода `dwAttrib` параметр должен соответствовать значению, возвращенному методом [OutAttribute](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) , как вызвано для объекта события, переданного в `pEvent` параметре.  
  
 Все события отладки публикуются асинхронно, независимо от того, является ли событие асинхронным или нет. Когда DE вызывает этот метод, возвращаемое значение не указывает, было ли событие обработано, только было ли получено событие. Фактически, в большинстве случаев событие не было обработано при возврате из этого метода.  
  
## <a name="see-also"></a>См. также:  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
