---
title: Связывание брейк-пойнтов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739230"
---
# <a name="bind-breakpoints"></a>Связать точки разрыва
Если пользователь устанавливает точку разрыва, возможно, нажав **F9,** IDE формулирует запрос и подсказывает сеанс отладки для создания точки разрыва.

## <a name="set-a-breakpoint"></a>Установка точки останова
 Установка точки разрыва — это двухэтапный процесс, поскольку код или данные, затронутые точкой разрыва, могут быть еще недоступны. Во-первых, точка разрыва должна быть описана, а затем, по мере поступления кода или данных, она должна быть привязана к этому коду или данным следующим образом:

1. Точка разрыва запрашивается у соответствующих отладительных двигателей (DE), а затем точка разрыва привязана к коду или данным по мере ее поступления.

2. Запрос точки разрыва отправляется на сеанс отладки, который отправляет его всем соответствующим DEs. Любой DE, который выбирает для обработки точки разрыва, создает соответствующую точку ожидания.

3. Сеанс отладки собирает ожидающие сячки и отправляет их обратно в пакет отладки (компонент отладки Visual Studio).

4. Пакет отладки побуждает сеанс отладки привязать отложенную точку разрыва к коду или данным. Сеанс отладки отправляет этот запрос всем соответствующим DEs.

5. Если DE способен связать точку разрыва, он отправляет событие, связанное с точкой разрыва, обратно в сеанс отладки. Если нет, он отправляет событие ошибки точки разрыва вместо этого.

## <a name="pending-breakpoints"></a>Ожидающие моменты разрыва
 Отложенная точка разрыва может связываться с несколькими местоположениями кода. Например, строка исходного кода для шаблона СЗ может связываться с каждой последовательностью кода, генерируемой из шаблона. Сеанс отладки может использовать событие, связанное с точкой разрыва, для перечисления контекстов кода, связанных с точкой разрыва во время отправки события. Дополнительные контексты кода могут быть связаны позже, поэтому DE может отправить несколько событий, связанных точками разрыва, для каждого запроса на связывание. Однако DE должен отправить только одно событие ошибки точки разрыва на запрос привязки.

## <a name="implementation"></a>Реализация
 Программно пакет отладки вызывает диспетчера отладки сеанса (SDM) и дает ему интерфейс [IDebugBreakpointRequest2,](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) который обертывает [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) структуру, которая описывает точку разрыва, которая должна быть установлена. Хотя точки разрыва могут быть разных форм, они в конечном счете решаются на контекст кода или данных.

 SDM передает этот вызов каждому соответствующему DE, позвонив в метод [CreatePendingBreakpoint.](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) Если DE выбирает для обработки точки разрыва, он создает и возвращает интерфейс [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) SDM собирает эти интерфейсы и передает их обратно в `IDebugPendingBreakpoint2` пакет отладки в качестве единого интерфейса.

 До сих пор никаких событий не было получено.

 Пакет отладки затем пытается связать отложенную точку разрыва с кодом или данными, вызывая [Bind,](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)который реализуется DE.

 Если точка разрыва связана, DE отправляет интерфейс события [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) в пакет отладок. Пакет отладки использует этот интерфейс для перечисления всех контекстов кода (или единого контекста данных), привязанных к точке разрыва, позвонив [в EnumBoundBreakpoints,](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)который возвращает один или несколько интерфейсов [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Интерфейс [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) возвращает интерфейс [IDebugBreakpointResolution2,](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) а [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) возвращает [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) союз, содержащий контекст кода или данных.

 Если DE не может связать точку разрыва, он отправляет один интерфейс события [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) в пакет отладок. Пакет отладки получает тип ошибки (ошибка или предупреждение) и информационное сообщение, позвонив [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), а затем [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) и [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Это возвращает [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) структуру, содержащую тип ошибки и сообщение.

 Если DE обрабатывает точку разрыва, но не может связать `BPET_TYPE_ERROR`ее, он возвращает ошибку типа. Пакет отладки отвечает, отображая поле диалога ошибок, и IDE помещает восклицательный глиф внутри глифа разрыва глифа слева от строки исходного кода.

 Если DE обрабатывает точку разрыва, не может связать ее, но некоторые другие DE могут связать ее, он возвращает предупреждение. IDE отвечает, размещая глиф-вопрос внутри точки разрыва глифа слева от строки исходного кода.

## <a name="see-also"></a>См. также
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
