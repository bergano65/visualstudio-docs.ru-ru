---
title: "Привязка точки останова | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 08000dddcd574d21225aa110cf9eb4ab2487aadb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="binding-breakpoints"></a>Привязка точки останова
Если пользователь устанавливает точку останова, возможно, нажав клавишу F9, IDE формирует запрос и предлагает сеанса отладки, чтобы создать точку останова.  
  
## <a name="setting-a-breakpoint"></a>Установка точки останова  
 Задание точки останова является в два этапа, из-за кода или данных, затронутые точки останова могут еще не быть доступными. Сначала должны быть описаны точки останова, а затем кода или данных становится доступной, она должна быть привязана к этого кода или данных, следующим образом:  
  
1.  Точка останова запрашивается из соответствующих отладчики (DEs) и затем точки останова связанный с кодом или данными, что она станет доступной.  
  
2.  Точка останова запрос отправляется в сеанс отладки, который отправляет его на всех соответствующих DEs. Любой DE, который выбирает для обработки точки останова создает соответствующий ожидающих точек останова.  
  
3.  Сеанс отладки собирает ожидающих точек останова и отправляет их обратно на отладочный пакет (компонент отладки Visual Studio).  
  
4.  Отладочный пакет запрашивает сеанса отладки, чтобы привязать ожидающая точка останова в коде или в данных. Сеанс отладки отправляет этот запрос на все соответствующие DEs.  
  
5.  Если DE сможет выполнять привязку точки останова, он отправляет привязанное событие точки останова обратно в сеансе отладки. В противном случае он отправляет событие ошибки точки останова.  
  
## <a name="pending-breakpoints"></a>Ожидающих точек останова  
 Ожидающая точка останова можно привязать несколько расположений кода. Например строки исходного кода для шаблонов C++ можно привязать к каждой последовательности кода, созданное на основе шаблона. Сеанс отладки можно использовать связанного события точки останова для перечисления контексты код, привязка точки останова во время отправки события. Несколько контекстов кода могут быть привязаны более поздней версии, поэтому DE могут отправлять несколько точек останова, связанный с событий для каждого запроса привязки. Тем не менее DE следует отправить только одно событие ошибки точки останова на запрос привязки.  
  
## <a name="implementation"></a>Реализация  
 Программно, отладочный пакет вызывает сеанса отладки (SDM) manager и ему [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) интерфейс, который создает оболочку для [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) структуру, которая описывает точка останова устанавливается. Несмотря на то, что точки останова могут быть различные формы, разрешены в конечном счете на контекст кода или данных.  
  
 SDM передает этот вызов для каждого соответствующего DE путем вызова его [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) метод. По желанию DE для обработки точки останова, он создает и возвращает [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейса. SDM собирает эти интерфейсы и передает их как один пакет отладки `IDebugPendingBreakpoint2` интерфейса.  
  
 На данный момент не созданы события отсутствуют.  
  
 Отладочный пакет пытается привязать ожидающая точка останова в коде или в данных, вызвав [привязки](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), который реализован DE.  
  
 Если точка останова имеет привязку, отправляет DE [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) интерфейс событий отладки пакет. Использует пакет отладки, этот интерфейс, чтобы перечислить все контексты кода (или контекст данных single) привязан к точке останова путем вызова [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), которая возвращает один или несколько [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) интерфейсов. [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) интерфейс возвращает [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) интерфейс, и [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) возвращает [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) объединение, содержащие контекст кода или данных.  
  
 Если не удается выполнить привязку точки останова DE, он отправляет один [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) интерфейс событий отладки пакет. Отладочный пакет получает тип ошибки (ошибка или предупреждение) и информационные сообщения, вызывая [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), за которым следует [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) и [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Возвращает [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) структуру, содержащую тип ошибки и сообщения.  
  
 Если DE обрабатывает точки останова, но его невозможно привязать, возвращается ошибка типа `BPET_TYPE_ERROR`. Отладочный пакет отвечает, отображая диалоговое окно ошибки, а IDE помещает глифа восклицательный знак внутри глиф точки останова до левой строке исходного кода.  
  
 Если DE обрабатывает точки останова, а не удается привязать его, но некоторые другие может привязать DE, возвращается предупреждение. IDE отвечает, поместив глиф вопрос внутри глиф точки останова до левой строке исходного кода.  
  
## <a name="see-also"></a>См. также  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)