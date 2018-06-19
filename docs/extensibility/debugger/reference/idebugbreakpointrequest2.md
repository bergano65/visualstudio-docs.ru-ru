---
title: IDebugBreakpointRequest2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03403a09ea5cd66839bf31fe5c690262fd55f3a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103313"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Этот интерфейс представляет сведения, необходимые для создания и привязки точки останова любого типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Диспетчер сеансов отладки (SDM) обычно реализует этот интерфейс.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Модуль отладки (DE) получает этого интерфейса через вызов [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) для создания ожидающая точка останова. Вызов [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) можно получить этот интерфейс из DE.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBreakpointRequest2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Возвращает тип местоположения точки останова запроса точки останова.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Возвращает сведения о точках останова запроса, описывающее этот запрос точки останова.|  
  
## <a name="remarks"></a>Примечания  
 После программа отлаживаемый был загружен, вызов [привязки](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) привязывает ожидающая точка останова в указанное место в программе.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)