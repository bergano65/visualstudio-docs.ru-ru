---
title: Поддерживаемые типы событий Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712803"
---
# <a name="supported-event-types"></a>Поддерживаемые типы событий
Отладка Visual Studio в настоящее время поддерживает следующие типы событий:

- Асинхронные события

   Сообщите диспетчеру отладки сеанса (SDM) и IDE о том, что состояние отладитого приложения меняется. Эти мероприятия обрабатываются в свободное время SDM и IDE. Ответ на отладку (DE) после обработки события не отправляется. Интерфейсы [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) и [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) являются примерами асинхронных событий.

- Синхронные события

   Сообщите SDM и IDE о том, что состояние отладки приложения меняется. Единственное различие между этими событиями и асинхронными событиями заключается в том, что ответ отправляется с помощью метода [ContinueFromSynusEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

   Отправка синхронного события полезна, если вам нужно, чтобы ваше DE продолжила обработку после получения и обработки события IDE.

- Синхронная остановка событий или остановка событий

   Сообщите SDM и IDE о том, что отладка приложения прекратила выполнение кода. При отправке события остановки с помощью метода [Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)требуется параметр [IDebugThread2.](../../extensibility/debugger/reference/idebugthread2.md) Остановка событий продолжается вызовом к одному из следующих методов:

  - [Выполнить](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Шаг](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Продолжить](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Интерфейсы [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) и [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) являются примерами остановки событий.

  > [!NOTE]
  > Асинхронные события остановки не поддерживаются. Это ошибка, чтобы отправить асинхронное событие остановки.

## <a name="discussion"></a>Обсуждение
 Фактическая реализация событий зависит от дизайна вашего DE. Тип отправленного события определяется его атрибутами, которые устанавливаются при проектировании DE. Например, один DE может отправить [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) как асинхронное событие, в то время как другой может отправить его в качестве события остановки.

 В следующей таблице указывается, какие параметры программы и потока необходимы для каких событий, а также типов событий. Любое событие может быть синхронным. Ни одно событие не должно быть синхронным.

> [!NOTE]
> Интерфейс [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) необходим для всех событий.

|Событие|IDebugProgram2|IDebugThread2|Остановка событий|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|нет|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Обязательно|Обязательно|Да|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|нет|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|нет|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|нет|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Обязательно|Обязательно|Да|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Обязательно|Обязательно|нет|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Не разрешено|Не разрешено|нет|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Не разрешено|Не разрешено|нет|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Обязательно|Обязательно|Да|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Может быть|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Обязательно|Обязательно|Да|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Может быть|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Обязательно|Обязательно|Да|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Обязательно|Обязательно|Да|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|Может быть|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Обязательно|Разрешено, но не требуется|нет|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|нет|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Обязательно|Разрешено, но не требуется|нет|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Обязательно|Разрешено, но не требуется|нет|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Обязательно|Разрешено, но не требуется|нет|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Обязательно|Разрешено, но не требуется|нет|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|нет|
|IDebugStopCompleteEvent2|Обязательно|Обязательно|Да|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Обязательно|Обязательно|Да|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|нет|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Обязательно|Обязательно|нет|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Обязательно|Обязательно|нет|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Разрешено, но не требуется|Разрешено, но не требуется|нет|

## <a name="see-also"></a>См. также
- [Отправка событий](../../extensibility/debugger/sending-events.md)
