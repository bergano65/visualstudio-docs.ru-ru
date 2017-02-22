---
title: "Поддерживаемые типы событий | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], поддерживаемые события"
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Поддерживаемые типы событий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio при отладке в настоящее время поддерживают следующие типы события:  
  
-   Асинхронные события  
  
     Уведомляет диспетчер сеанс отладки \(SDM\) и интегрированная среда разработки, которая изменяет состояние отлаживаемого приложения.  Эти события обрабатываются на отдыхе SDM и интегрированной среды разработки.  Ответ не передается в обработчик отладки \(DE\) как только событие обрабатывается.  [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) и  [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) интерфейсы примеры асинхронных событий.  
  
-   Синхронные события  
  
     SDM и уведомлять среду разработки, что состояние отлаживаемого приложения изменяется.  Единственное различие между этими двумя событиями и асинхронными событиями, что ответ отправляется с помощью [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) метод.  
  
     Отправка синхронное событие полезно, если требуется пользовательский DE продолжать обработку после интегрированная среда разработки получает и обрабатывает событие.  
  
-   Синхронных событий остановки или при остановке события  
  
     SDM и уведомлять среду разработки, что отлаживаемый остановку выполнения кода приложения.  При отправке при остановке событие посредством метода [Событие](../../extensibility/debugger/reference/idebugeventcallback2-event.md)"  [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) параметр является обязательным.  Остановка события продолжены вызова один из следующих методов:  
  
    -   [Выполнение](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Шаг](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Интерфейсы [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) и  [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) примеры остановить события.  
  
    > [!NOTE]
    >  Асинхронный при остановке событий не поддерживается.  Ошибка при остановке отправлять асинхронное событие.  
  
## Обсуждение  
 Фактическая реализация зависит от конструкции вашего DE событий.  Тип каждого оправляемого события определяется ее атрибутами, которые устанавливаются при проектировании DE.  Например, один DE может отправлять IDebugProgramCreateEvent2 как асинхронное событие, а другие могут отправлять их как при остановке событие.  
  
 Следующая таблица определяет, какие параметры программы и потока требуются для которых события, а также типов событий.  Любое событие может быть одновременно.  Нет событие не требуется одновременно.  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) интерфейс, необходимый для всех событий.  
  
|Событие|IDebugProgram2|IDebugThread2|Остановка события|  
|-------------|--------------------|-------------------|-----------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Нет|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Требуется|Требуется|Да|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Нет|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Нет|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Нет|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Требуется|Требуется|Да|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Требуется|Требуется|Нет|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Недопустимо|Недопустимо|Нет|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Недопустимо|Недопустимо|Нет|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Требуется|Требуется|Да|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Может быть|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Требуется|Требуется|Да|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Может быть|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Требуется|Требуется|Да|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Требуется|Требуется|Да|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Может быть|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Требуется|Разрешено, но не является обязательным|Нет|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Нет|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Требуется|Разрешено, но не является обязательным|Нет|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Требуется|Разрешено, но не является обязательным|Нет|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Требуется|Разрешено, но не является обязательным|Нет|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Требуется|Разрешено, но не является обязательным|Нет|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Нет|  
|IDebugStopCompleteEvent2|Требуется|Требуется|Да|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Требуется|Требуется|Да|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Нет|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Требуется|Требуется|Нет|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Требуется|Требуется|Нет|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Разрешено, но не является обязательным|Разрешено, но не является обязательным|Нет|  
  
## См. также  
 [Отправка событий](../../extensibility/debugger/sending-events.md)