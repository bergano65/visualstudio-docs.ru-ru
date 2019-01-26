---
title: IDebugBreakpointUnboundEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointUnboundEvent2
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14a16080424ae19e909751a797a49192a22e645d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947872"
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
Этот интерфейс указывает диспетчер отладки сеансов (SDM), в том, что связанная точка останова был отсоединен от загрузки программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс как часть поддержки точек останова. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс).  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 DE создает и отправляет этот объект события, когда связанная точка останова была не связанного с данными. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, если он присоединен к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBreakpointUnboundEvent2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Возвращает точку останова, которые стали свободной.|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Получает причину, по которой был отсоединен точки останова.|  
  
## <a name="remarks"></a>Примечания  
 При выгрузке модуля отладки библиотеки DLL или класс, все точки останова, которые были привязаны к код этого модуля должен быть отсоединен от отлаживаемой программы. `IDebugBreakpointUnboundEvent2` Отправляется для каждого несвязанного точки останова.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)