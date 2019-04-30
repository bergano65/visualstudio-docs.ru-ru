---
title: Связывание точек останова | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c36e5df52d4caa34d611f7f1c26b8a5187a637a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926088"
---
# <a name="bind-breakpoints"></a>Привязка точки останова
Если пользователь устанавливает точку останова, возможно, нажав клавишу **F9**, среда IDE формирует запрос и запрашивает у сеанса отладки, чтобы создать точку останова.

## <a name="set-a-breakpoint"></a>Установка точки останова
 Задание точки останова — это двухэтапный процесс, так как код или данные, влияет точка останова, еще недоступен. Во-первых точки останова должны быть описаны, и затем, как кода или данных становится доступной, она должна быть привязана к этого кода или данных, следующим образом:

1. Точка останова запрашивается из соответствующих отладчики (DEs) и затем точку останова связанный код или данные, что она станет доступной.

2. Точка останова запрос отправляется в сеанс отладки, который отправляет его на всех соответствующих DEs. Любой DE, выбирает для обработки точки останова создает соответствующий ожидающих точек останова.

3. Сеанс отладки собирает ожидающих точек останова и отправляет их обратно на отладочный пакет (компонент отладки Visual Studio).

4. Размер пакета отладки запрашивает сеанса отладки для привязки к коду или данным ожидающая точка останова. Сеанс отладки отправляет этот запрос на все соответствующие DEs.

5. Если DE способен выполнять привязку точки останова, отправленному им точку останова привязки событий к сеансу отладки. Если нет, он отправляет событие ошибки точки останова.

## <a name="pending-breakpoints"></a>Ожидающих точек останова
 Ожидающая точка останова можно привязать несколько расположений кода. Например строки исходного кода для шаблонов C++ можно привязать к каждой последовательности кода, созданное на основе шаблона. Сеанс отладки можно использовать точки останова привязанных событий для перечисления контекстов кода, привязываются к точке останова во время отправки события. Несколько контекстов кода могут быть связаны более поздней версии, поэтому DE могут отправлять события для каждого запроса привязки, связанный с нескольких точек останова. Тем не менее DE должны отправлять только одно событие ошибки точки останова в запрос на привязку.

## <a name="implementation"></a>Реализация
 Программным образом, размер пакета отладки вызывает сеанса отладки manager (SDM) и присваивает ему [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) интерфейс, который заключает в оболочку [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) структуру, которая описывает точка останова устанавливается. Несмотря на то, что точки останова могут быть различные формы, в конечном счете клиенты преобразуют контекст кода или данных.

 SDM передает этот вызов для каждого соответствующего DE путем вызова его [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) метод. Если DE выбирает для обработки точки останова, он создает и возвращает [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейс. SDM собирает эти интерфейсы и передает их обратно в отладочный пакет как одиночный `IDebugPendingBreakpoint2` интерфейс.

 На данный момент не созданы нет событий.

 Размер пакета отладки затем пытается выполнить привязку ожидающая точка останова для кода или данных, вызвав [привязать](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), реализованная DE.

 Если точка останова привязаны, DE отправляет [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) интерфейс событий для пакета отладки. Использует пакет отладки, этот интерфейс для перечисления всех контекстов кода (или контекст данных single) привязан до точки останова, вызвав [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), который возвращает один или несколько [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) интерфейсов. [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) интерфейс возвращает [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) интерфейс, и [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) возвращает [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) union, содержащий контекст кода или данных.

 Если DE не сможет выполнять привязку точки останова, он отправляет отдельный [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) интерфейс событий для пакета отладки. Отладочный пакет получает тип ошибки (ошибка или предупреждение) и информационные сообщения, вызывая [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), за которым следует [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) и [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Эта команда возвращает [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) структуру, содержащую тип ошибки и сообщение.

 Если DE обрабатывает точки останова, но его невозможно привязать, возвращается ошибка типа `BPET_TYPE_ERROR`. Размер пакета отладки отвечает отобразив диалоговое окно ошибки, а интегрированной среды разработки помещает глиф в виде восклицательного знака внутри глиф точки останова слева от строке исходного кода.

 Если DE обрабатывает точки останова, а не удается привязать его, но другой DE может привязать его, возвращается предупреждение. Интегрированная среда разработки отвечает, поместив глиф вопрос внутри глиф точки останова слева от строке исходного кода.

## <a name="see-also"></a>См. также
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)