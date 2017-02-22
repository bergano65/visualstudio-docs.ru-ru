---
title: "IDebugEventCallback2::Event | Microsoft Docs"
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
  - "IDebugEventCallback2::Event"
helpviewer_keywords: 
  - "IDebugEventCallback2::Event"
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Отправляет уведомление отладочные события.  
  
## Синтаксис  
  
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
  
```c#  
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
  
#### Параметры  
 `pEngine`  
 \[in\] [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) объект, представляющий обработчик отладки \(DE\), отправляющего это событие.  Требуются заполняет DE этот параметр.  
  
 `pProcess`  
 \[in\] IDebugProcess2 объект, представляющий процесс, в котором произошло событие.  Этот параметр заполняется в сеансе отладки \(SDM manager\).  DE всегда передает значение NULL для этого параметра.  
  
 `pProgram`  
 \[in\] IDebugProgram2 объект, представляющий программы, в которой это событие возникает.  Для большинства событий, этот параметр имеет значение NULL.  
  
 `pThread`  
 \[in\] IDebugThread2 объект, представляющий поток, в котором событие происходит.  Для остановки события, этот параметр не может принимать значение NULL, так как кадр стека получен от данного параметра.  
  
 `pEvent`  
 \[in\] IDebugEvent2 объект, представляющий событие отладки.  
  
 `riidEvent`  
 \[in\] идентификатор GUID, определяющий, интерфейс событий, получаемых из `pEvent` параметр.  
  
 `dwAttrib`  
 \[in\] сочетание пометит из [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) перечисление.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 При вызове этого метода `dwAttrib` параметр должен соответствовать значению, возвращенному из  [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) метод вызывается на объекте, переданном в событий  `pEvent` параметр.  
  
 Все отладочные события создаются асинхронно независимо от того, является ли событие само асинхронно.  DE при вызове этого метода возвращаемое значение показывает, было ли обработано событие не только было получено ли событие.  В действительности в большинстве случаев не было обработано событие при возвращении данного метода.  
  
## См. также  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)