---
title: IDebugEventCallback2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6114a31701e5abc4714f315b4e4f1ecf022c401c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163814"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс используется модулем отладки (DE) для отправки событий отладки в Диспетчер отладки сеансов (SDM).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] реализует этот интерфейс для получения событий от модуля отладки.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Модуль отладки обычно получает этот интерфейс, когда SDM вызывает [Присоединение](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md)или [лаунчсуспендед](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Модуль отладки отправляет события в SDM, вызывая [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEventCallback2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Отправляет уведомление о событиях отладки в SDM.|  
  
## <a name="remarks"></a>Remarks  
 Хотя [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) указывают, что они принимают `IDebugEventCallback2` интерфейс, это не так, а указатель интерфейса всегда будет иметь значение null. Вместо этого модуль отладки должен использовать интерфейс, `IDebugEventCallback2` полученный в вызове для [присоединения](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [присоединения](../../../extensibility/debugger/reference/idebugengine2-attach.md)или [лаунчсуспендед](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Если пакет реализует [идебужевенткаллбакк](../../../extensibility/debugger/reference/idebugeventcallback2.md) в управляемом коде, настоятельно рекомендуется <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> вызывать его для различных интерфейсов, передаваемых в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [лаунчсуспендед](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Вновь](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
