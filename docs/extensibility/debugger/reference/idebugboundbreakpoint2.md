---
title: IDebugBoundBreakpoint2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a37f637e77c342b3af977884241d0e922ac6aaa6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Этот интерфейс представляет точку останова, к которому привязан расположения в коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки точек останова.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [привязки](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создает этот интерфейс. Вызовы [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) и [Далее](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) можно также получить этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBoundBreakpoint2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Возвращает ожидающая точка останова, из которой был создан указанный связанная точка останова.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Получает состояние данная связанная точка останова.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Возвращает текущий счетчик числа попаданий для данная связанная точка останова.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Возвращает разрешение точки останова, описывающий эту точку останова.|  
|[Включить](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Включение или отключение точки останова.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Задает число попаданий для данная связанная точка останова.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Задает или изменяет условие, связанное с данная связанная точка останова.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Наборы или изменения, число прохода, связанного с данная связанная точка останова.|  
|[Удалить](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет точку останова.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)