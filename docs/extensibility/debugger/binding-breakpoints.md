---
title: "Привязка точки останова | Microsoft Docs"
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
  - "Привязка точек останова"
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Привязка точки останова
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Если пользователь задает точку останова, возможно, нажав клавишу F9, интегрированная среда разработки формулируют запрос и запрашивают сеанс отладки создать точку останова.  
  
## Установка точки останова  
 Установка точки останова процесс 2, поскольку код или данные, на которые влияет точкой останова могут быть доступны не во время.  Во\-первых, необходимо описать точку останова, а затем по мере того, как код или данные становятся доступными, их необходимо привязать к этим данным или коду, следующим образом:  
  
1.  Точка останова запрошено, из соответствующего обработчики отладки \(triple data encryption standard\), затем точка останова кода или привязана к данным, так как она становится доступной.  
  
2.  Запрос отправляется в сеанс отладки, точки останова, который отправляет его ко всему соответствующий DEs.  Любой DE, который выбирает для обработки точку останова, соответствующие ожидающие точки останова.  
  
3.  Сеанс отладки собираются ожидающих точки останова и отправляет их обратно к пакету отладки \(компоненту отладки Visual Studio\).  
  
4.  Пакет отладки предлагает сеанс отладки привязки отложенную точку останова в код или данные.  Сеанс отладки отправляет запрос ко всему соответствующий DEs.  
  
5.  Если DE удается привязать точка останова, он отправляет событие точки останова обратно к сеансу отладки server.  Если нет, то он отправляет событие ошибки точки останова.  
  
## Ожидающие точки останова  
 Ожидается точка останова может выполнить привязку к разным местам кода.  Например, линия исходного кода для шаблона c\+\+ может выполнить привязку к каждой последовательности кода, созданных из шаблона.  Сеанс отладки может использовать событие точки останова связанное для перечисления контексты кода, привязанные к точке останова на момент событие было отправлено.  Несколько контекстов кода можно привязать более поздних версиях, поэтому DE может отправлять события, связанные с множественной точки останова для каждого запроса привязки.  Однако DE должен отправлять только одно событие ошибки точки останова в запрос привязки.  
  
## Реализация  
 Пакет программным образом, отладка вызывает сеанс отладки \(SDM\) диспетчер и присваивает ему [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) интерфейс, который создает программу\-оболочку a  [BP\_REQUEST\_INFO](../../extensibility/debugger/reference/bp-request-info.md) структура, описывающая точку останова, чтобы быть задана.  Хотя точки останова могут принимать множество разных форм, их в конечном счете позволяют к контексту кода или данных.  
  
 SDM передает этот вызов к каждому путем вызова его соответствующий DE [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) метод.  Если DE выбирает для обработки точку останова, то он создает и возвращает IDebugPendingBreakpoint2 интерфейс.  SDM собирает эти интерфейсы и передает их обратно к пакету отладки, как отдельное `IDebugPendingBreakpoint2` интерфейс.  
  
 На данный момент запись событий не были созданы.  
  
 Пакет пытается выполнить отладку затем ожидается точка останова в код или данные путем вызова [Привязка](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), которая реализуется DE.  
  
 Если точка останова, то отправляет привязана DE IDebugBreakpointBoundEvent2 интерфейс событий к пакету отладки.  Пакет отладки использует этот интерфейс для перечисления всех контекстах кода \(или один контекст данных\) привязанные к точке останова, вызывая [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), который возвращает один или несколько  [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) интерфейсы.  [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) возвращает интерфейс  [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) интерфейс и  [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) возвращает a  [BP\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) объединение, содержащий контекст кода или данных.  
  
 Если DE удалось привязать точка останова, он отправляет отдельный IDebugBreakpointErrorEvent2 интерфейс событий к пакету отладки.  Пакет извлекает тип ошибки отладки \(ошибку или предупреждение\) и информационное сообщение, вызвав [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), за которым следуют  [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) и  [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md).  Это возвращает a [BP\_ERROR\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) структура, содержащая тип и сообщение об ошибке.  
  
 Если DE маркер точки останова, но не удается привязать его, он возвращает ошибку типа `BPET_TYPE_ERROR`.  Пакет отладки отвечает, отображение диалогового окна ошибок и интегрированная среда разработки устанавливает глиф восклицания внутри глифа слева от точки останова линии исходного кода.  
  
 Если DE маркер точки останова не удается привязать его, но какой\-либо другой DE может привязать он возвращается предупреждение.  Интегрированная среда разработки отвечает, установив глиф вопроса в глифа слева от точки останова линии исходного кода.  
  
## См. также  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)