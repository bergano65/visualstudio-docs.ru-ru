---
title: IDebugBoundBreakpoint2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad36363ff20e285dde2db6fc723ddf2562c491f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156165"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет точку останова, которая привязана к расположение кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс как часть поддержки точек останова.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [привязать](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создает этот интерфейс. Вызовы [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) и [Далее](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) можно также получить этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBoundBreakpoint2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Получает ожидающая точка останова, из которого был создан указанного связанная точка останова.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Получает состояние данная связанная точка останова.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Возвращает текущий счетчик числа попаданий для данная связанная точка останова.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Получает разрешение точек останова, который описывает эту точку останова.|  
|[Enable](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Включает или отключает точку останова.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Задает количество обращений к данная связанная точка останова.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Задает или изменяет условие, связанное с данная связанная точка останова.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Наборы или изменения счетчик pass, связанного с данная связанная точка останова.|  
|[Удаление](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет точку останова.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
