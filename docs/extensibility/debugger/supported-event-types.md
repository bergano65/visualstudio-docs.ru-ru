---
title: Поддерживаемые типы событий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6b308aabacf5a82f4ea630ccae256c56526f793
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="supported-event-types"></a>Поддерживаемые типы событий
В настоящее время отладки Visual Studio поддерживает следующие типы событий:  
  
-   Асинхронных событий  
  
     Уведомлять диспетчера сеанса отладки (SDM) и IDE, изменения состояния отлаживаемого приложения. Эти события обрабатываются на удобное SDM и интегрированной среды разработки. Ответ не отправляется в модуль отладки (DE), после обработки события. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) и [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) интерфейсы являются примерами асинхронных событий.  
  
-   Синхронные события  
  
     Уведомите SDM и IDE, изменения состояния отлаживаемого приложения. Единственное различие между эти события и асинхронные события —, ответ отправляется с помощью параметра [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) метод.  
  
     Отправка синхронных событий полезно в том случае, если необходимо, чтобы ваш DE для продолжения обработки после IDE получает и обрабатывает событие.  
  
-   Синхронные события остановки, или события остановки  
  
     Уведомите SDM и интегрированной среды разработки, что отлаживаемого приложения было остановлено выполнение кода. При отправке события остановки с помощью метода [событий](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) параметр является обязательным. Остановка события унаследованные путем вызова одного из следующих методов:  
  
    -   [Выполнение](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Интерфейсы [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) и [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) являются примерами событий остановки.  
  
    > [!NOTE]
    >  Остановка асинхронных событий не поддерживаются. Это ошибка Отправить событие остановки асинхронной.  
  
## <a name="discussion"></a>Обсуждение  
 Фактическую реализацию события зависит от вида вашей DE. Тип каждое событие, отправленное определяется его атрибутов, которые настраиваются при конструировании DE. Например, могут отправлять одно DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) как асинхронные события, пока другой может отправить как событие остановки.  
  
 Следующая таблица указывает, какие программы и поток параметры являются обязательными для какие события, а также типы событий. Любые события могут быть синхронными. Событие не должен быть синхронным.  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) интерфейса является обязательным для всех событий.  
  
|событие|IDebugProgram2|IDebugThread2|События остановки|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Нет|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Нет|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Нет|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Нет|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Обязательно|Обязательно|Нет|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Не допускается|Не допускается|Нет|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Не допускается|Не допускается|Нет|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Может быть|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Может быть|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Может быть|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Обязательно|Может быть, но не обязательно|Нет|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Нет|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Обязательно|Может быть, но не обязательно|Нет|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Обязательно|Может быть, но не обязательно|Нет|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Обязательно|Может быть, но не обязательно|Нет|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Обязательно|Может быть, но не обязательно|Нет|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Нет|  
|IDebugStopCompleteEvent2|Обязательно|Обязательно|Да|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Нет|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Обязательно|Обязательно|Нет|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Обязательно|Обязательно|Нет|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Может быть, но не обязательно|Может быть, но не обязательно|Нет|  
  
## <a name="see-also"></a>См. также  
 [Отправка событий](../../extensibility/debugger/sending-events.md)