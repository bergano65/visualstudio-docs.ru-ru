---
title: Поддерживаемые типы событий | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 846a889a22188249a1a42e8d66f0b3730a19dfc2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228765"
---
# <a name="supported-event-types"></a>Поддерживаемые типы событий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отладка в Visual Studio в настоящее время поддерживает следующие типы событий:  
  
-   Асинхронные события  
  
     Уведомить диспетчер отладки сеансов (SDM) и IDE, изменения состояния отлаживаемого приложения. Эти события обрабатываются в свободное время, SDM и интегрированной среды разработки. Ответ не отправляется в модуль отладки (DE), после обработки события. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) и [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) интерфейсы являются примерами асинхронные события.  
  
-   Синхронные события  
  
     Уведомите SDM и IDE, изменения состояния отлаживаемого приложения. Единственное различие между эти события и асинхронные события является, что ответ отправляется с помощью параметра [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) метод.  
  
     Отправка синхронных событий полезно в том случае, если необходимо, чтобы ваш DE, чтобы продолжить обработку после интегрированной среды разработки, получает и обрабатывает событие.  
  
-   Синхронные события остановки "или" Остановка событий  
  
     Уведомите SDM и интегрированной среды разработки, что отлаживаемого приложения прекратила выполнение кода. При отправке событии остановки с помощью метода [событий](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) параметр является обязательным. Остановка события унаследованные путем вызова одного из следующих методов:  
  
    -   [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Интерфейсы [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) и [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) являются примерами событий остановки.  
  
    > [!NOTE]
    >  Остановка асинхронных событий не поддерживаются. Это ошибка для отправки события асинхронной остановки.  
  
## <a name="discussion"></a>Обсуждение  
 Фактическую реализацию событий зависит от структуры вашей DE. Тип каждое событие, отправленное определяется его атрибутов, которые настраиваются при создании DE. Например, может отправить один DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) как событие асинхронной, то время как другой может отправлять как событие остановки.  
  
 В следующей таблице указано, какие программы и поток параметры являются обязательными для какие события, а также типы событий. Любое событие может быть синхронным. Событие не должен быть синхронными.  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) он необходим для всех событий.  
  
|событие|IDebugProgram2|IDebugThread2|События остановки|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Нет|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Нет|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Нет|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Нет|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Обязательно|Обязательно|Нет|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Не допускается|Не допускается|Нет|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Не допускается|Не допускается|Нет|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Может быть|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Может быть|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Может быть|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Обязательно|Разрешено, хотя и не требуется|Нет|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Нет|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Обязательно|Разрешено, хотя и не требуется|Нет|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Обязательно|Разрешено, хотя и не требуется|Нет|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Обязательно|Разрешено, хотя и не требуется|Нет|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Обязательно|Разрешено, хотя и не требуется|Нет|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Нет|  
|IDebugStopCompleteEvent2|Обязательно|Обязательно|Да|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Обязательно|Обязательно|Да|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Нет|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Обязательно|Обязательно|Нет|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Обязательно|Обязательно|Нет|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Разрешено, хотя и не требуется|Разрешено, хотя и не требуется|Нет|  
  
## <a name="see-also"></a>См. также  
 [Отправка событий](../../extensibility/debugger/sending-events.md)

