---
title: IDebugEventCallback2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68d29d928f310cb045ed712a151f9275446465a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116208"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Этот интерфейс используется подсистема отладки (DE) для отправки событий отладки диспетчера сеанса отладки (SDM).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] реализует этот интерфейс для получения событий из модуля отладки.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Модуль отладки обычно получает этот интерфейс, когда вызывает SDM [присоединение](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md), или [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Модуль отладки отправляет события SDM путем вызова [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEventCallback2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Отправляет уведомление SDM событий отладки.|  
  
## <a name="remarks"></a>Примечания  
 Несмотря на то что [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) указать, что они принимают `IDebugEventCallback2` интерфейса, это не так, и указатель на интерфейс всегда будет иметь значение null. Вместо этого необходимо использовать модуль отладки `IDebugEventCallback2` получено при вызове интерфейса [присоединение](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md), или [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Если пакет реализует [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) в управляемом коде, настоятельно рекомендуется, <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> можно вызывать для различных интерфейсов, которые передаются [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Присоединение](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)