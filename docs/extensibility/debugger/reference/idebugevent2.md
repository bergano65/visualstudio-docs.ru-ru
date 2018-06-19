---
title: IDebugEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aff8be869bd65def16ca0519f7c87ea82320bb99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111214"
---
# <a name="idebugevent2"></a>IDebugEvent2
Этот интерфейс используется для взаимодействия критических отладочную информацию, например остановку в точке останова и некритических сведения, такие как сообщение отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) и поставщика пользовательский порт реализовать этот интерфейс на один и тот же объект в других интерфейсах событий.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 С помощью интерфейса IID интерфейса, аргумент, заданный для [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) или [событий](../../../extensibility/debugger/reference/idebugportevents2-event.md), диспетчер отладочной сеанса (SDM) вызывает [QueryInterface](/cpp/atl/queryinterface) на `IDebugEvent2` интерфейс для получения интерфейс соответствующее событие.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEvent2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Получает атрибуты для этого события отладки.|  
  
## <a name="remarks"></a>Примечания  
 Интерфейсы более конкретные события, такие как [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), не являющиеся производными от интерфейса IDebugEvent2, но вместо этого реализован как отдельный интерфейс на один и тот же объект как `IDebugEvent2`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)