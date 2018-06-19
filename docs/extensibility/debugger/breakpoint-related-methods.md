---
title: Методы, связанные с точки останова | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce44a7d3d3578d5157bcefcf14172d92ece677d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107294"
---
# <a name="breakpoint-related-methods"></a>Методы, связанные с точки останова
Отладчик (DE) должны поддерживать параметр точек останова. Отладка Visual Studio поддерживает следующие типы точек останова:  
  
-   Привязки  
  
     Запрашивается в пользовательском Интерфейсе и успешно привязать расположение указанного кода  
  
-   Не завершен  
  
     Запрошен через пользовательский Интерфейс, но не привязана к фактическое инструкции  
  
## <a name="discussion"></a>Обсуждение  
 Например ожидающая точка останова происходит при инструкции еще не загружены. После загрузки кода, ожидающих точек останова try для привязки к кода на месте своих, то есть, для вставки разрыва инструкций в коде. Отправка событий в Диспетчер сеанса отладки (SDM) для указания успешной привязки или для уведомления о том, что отсутствуют ошибки привязки.  
  
 Ожидающая точка останова также управляет внутреннего списка соответствующих связанных точек останова. Один ожидающий точка останова может привести к вставки множество точек останова в коде. Отладки пользовательского интерфейса Visual Studio показано древовидное представление ожидающих точек останова и соответствующие им привязку точки останова.  
  
 Создание и использование ожидающих точек останова требуется реализация [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) метода, а также следующие методы [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейсов.  
  
|Метод|Описание|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет, является ли заданное ожидающих точек останова можно привязать к расположения в коде.|  
|[BIND](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Привязывает указанный ожидающих точек останова одно или несколько расположений кода.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Получает состояние ожидающая точка останова.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Возвращает точку останова запрос, используемый для создания ожидающая точка останова.|  
|[Включить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает состояние выполнения ожидающая точка останова.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки останова, привязанный из ожидающая точка останова.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Перечисляет все точки останова ошибки, возникающие в результате ожидающая точка останова.|  
|[Удалить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Удаляет ожидающая точка останова и все точки останова, привязанный из него.|  
  
 Для перечисления связанных точек останова и точек останова ошибок, необходимо реализовать все методы [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) и [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Ожидающих точек останова, которые привязаны к коду расположение требует реализации следующих [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Возвращает ожидающая точка останова, которая содержит точку останова.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Получает состояние связанная точка останова.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Возвращает точку останова разрешение, описывающее точку останова.|  
|[Включить](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Включает или отключает точку останова.|  
|[Удалить](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет связанная точка останова.|  
  
 Разрешение и запроса информации требует реализации из следующих [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Получает тип точки останова, представленный разрешением.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о точках останова разрешение, описывающее точку останова.|  
  
 Устранение ошибок, которые могут возникнуть во время привязки необходимо реализовать следующие [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Возвращает ожидающая точка останова, содержащий точку останова по ошибке.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Возвращает разрешение ошибки точки останова, описывающий ошибки точки останова.|  
  
 Устранение ошибок, которые могут возникнуть во время привязки также требует следующих методов [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Получает тип точки останова.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешении точки останова.|  
  
 Просмотр исходного кода в точке останова необходимо реализовать методы [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) и/или методы [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)