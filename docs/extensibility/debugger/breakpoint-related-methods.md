---
title: Методы, связанные с брейк-пойнтами Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739206"
---
# <a name="breakpoint-related-methods"></a>Методы, связанные с брейк-пойнтами
Двигатель отладки (DE) должен поддерживать настройку точек разрыва. Отладка Visual Studio поддерживает следующие типы точек разрыва:

- Bound

     Запрос через uI и успешно привязан к определенному местоположению кода

- Ожидает

     Запрос через uI, но еще не привязан к фактическим инструкциям

## <a name="discussion"></a>Обсуждение
 Например, точка разрыва находится в ожидании, когда инструкции еще не загружены. При загрузке кода ожидающие поломки пытаются привязаться к коду в установленном месте, то есть вставить инструкции по взлому в код. События отправляются менеджеру отладки сеанса (SDM) для указания успешной привязки или уведомления о наличии обязательных ошибок.

 Ожидающий момент разрыва также управляет собственным внутренним списком соответствующих связанных моментов разрыва. Одна нерешенная точка разрыва может привести к вставке многих моментов разрыва в коде. Отладка uI Visual Studio показывает представление дерева ожидающих точек разрыва и соответствующих связанных точек разрыва.

 Создание и использование ожидающих моментов разрыва требуют реализации метода [IDebugEngine2::CreatePendingBreakpoint,](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) а также следующих методов интерфейсов [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

|Метод|Описание|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет, может ли указанная точка доступа к моменту ожидания связываться с местоположением кода.|
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Связывает указанную точку разрыва с одним или несколько местами кода.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Получает состояние ожидающего разрыва.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Получает запрос точки разрыва, используемый для создания ожидающего разрыва.|
|[Включение](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает включенное состояние ожидающего разрыва.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки разрыва, связанные с ожидавшей разрыва.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Перечисляет все точки ошибки, которые являются результатом отложенной точки разрыва.|
|[Удалить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Удаляет отложенную точку разрыва и все точки разрыва, связанные с ней.|

 Чтобы перечислить связанные точки разрыва и точки ошибки, необходимо реализовать все методы [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) и [IEnumDebugErrorBreakpoints2.](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)

 В ожидании моментов разрыва, которые связываются с местоположением кода, требуется реализация следующих методов [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

|Метод|Описание|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Получает ожидаемную точку разрыва, содержащую точку разрыва.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Получает состояние свяжей точки разрыва.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Получает разрешение точки разрыва, описывающая точку разрыва.|
|[Включение](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Позволяет или отсваивает точку разрыва.|
|[Удалить](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет точку разрыва.|

 Информация о разрешении и запросе требует реализации следующих методов [IDebugBreakpointResolution2.](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

|Метод|Описание|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Получает тип точки разрыва, представленную разрешением.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Получает информацию о разрешении точки разрыва, описывающая точку разрыва.|

 Разрешение ошибок, которые могут возникнуть во время связывания, требует реализации следующих методов [IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

|Метод|Описание|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Получает ожидачную точку разрыва, содержащую точку разрыва ошибки.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Получает разрешение ошибки точки разрыва, описывающая точку разрыва ошибки.|

 Разрешение ошибок, которые могут возникнуть во время связывания, также требует следующих методов [IDebugErrorBreakpointResolution2.](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)

|Метод|Описание|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Получает тип точки разрыва.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Получает информацию о разрешении точки разрыва.|

 Просмотр исходного кода в точке разрыва требует реализации методов [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) и/или методов [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>См. также
- [Контроль исполнения и государственная оценка](../../extensibility/debugger/execution-control-and-state-evaluation.md)
