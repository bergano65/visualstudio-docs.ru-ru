---
title: "IDebugBoundBreakpoint2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3406c6b415523ff8ec46b71b649a81a44fb01c66
ms.lasthandoff: 02/22/2017

---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Этот интерфейс представляет точку останова, которая привязана к расположение кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Отладчик (DE) реализует этот интерфейс как часть поддержки точек останова.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [привязать](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создает этот интерфейс. Вызовы [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) и [Далее](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) можно также получить этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBoundBreakpoint2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Возвращает ожидающая точка останова, из которой был создан указанный связанная точка останова.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Возвращает состояние этого связанная точка останова.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Возвращает текущий счетчик числа попаданий для этого связанная точка останова.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Возвращает разрешение точки останова, описывающий эту точку останова.|  
|[Включить](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Включение или отключение точки останова.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Задает число попаданий для этого связанная точка останова.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Задает или изменяет условие, связанное с этой связанная точка останова.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Задает или изменения количества pass, связанного с этой связанная точка останова.|  
|[Удаление](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет точку останова.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Привязка](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
