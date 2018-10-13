---
title: IDebugEventCallback2 | Документация Майкрософт
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
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5517050ffba73ae495300a5d32d40fd8dbc7c57c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226256"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс используется ядром отладки (DE) для отправки событий отладки в диспетчер отладки сеансов (SDM).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] реализует этот интерфейс для получения событий из модуля отладки.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Модуль отладки обычно получает этот интерфейс, когда вызывает SDM [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), или [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Модуль отладки отправляет события в SDM, вызвав [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEventCallback2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Отправляет уведомление отладки событий SDM.|  
  
## <a name="remarks"></a>Примечания  
 Несмотря на то что [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) указать, что они принимают `IDebugEventCallback2` интерфейса, это не так, и указатель интерфейса всегда будет иметь значение null. Вместо этого необходимо использовать модуль отладки `IDebugEventCallback2` интерфейса получен в вызове [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), или [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Если пакет реализует [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) в управляемом коде, настоятельно рекомендуется, <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> можно вызывать для различных интерфейсов, которые передаются [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Присоединение](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)

