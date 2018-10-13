---
title: IDebugPendingBreakpoint2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85d73b3718a1afc2d9de7d9d5618749e2d85b13e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263605"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет точку останова, которая готова для привязки к расположение кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс как часть поддержки точек останова.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) создает точку останова из [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) интерфейс. Вызов [привязать](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) создает `IDebugBreakpoint2` интерфейс, который представляет связанная точка останова в программе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugPendingBreakpoint2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет ли этот ожидающая точка останова можно привязать к расположение кода.|  
|[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Связывает этот ожидающая точка останова одно или несколько расположений кода.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Получает состояние данного ожидающих точек останова.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Возвращает точки останова запрос, который был использован для создания этого ожидающая точка останова.|  
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Переключает виртуализированных состояние это ожидающих точек останова.|  
|[Enable](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает состояние объекта ожидающих точек останова.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Задает или изменяет условие, связанное с этим ожидающих точек останова.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Задает или изменяет число pass, связанные с данным ожидающим точки останова.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки останова, привязанный из этого ожидающая точка останова.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Перечисляет все точки останова ошибки, вызванные этой ожидающая точка останова.|  
|[Удалить](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Удаляет этот ожидающая точка останова и все точки останова, привязанный из него.|  
  
## <a name="remarks"></a>Примечания  
 `IDebugPendingBreakpoint2` может рассматриваться как поставщик все необходимые сведения, необходимые для привязки точку останова для кода, которые могут применяться для одного или нескольких программ.  
  
 Ожидающая точка останова потенциально может привести к более чем одной связанная точка останова. Например точки останова в стиле C++ шаблона может привести к связанная точка останова для каждого уникального экземпляра этого шаблона.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)

