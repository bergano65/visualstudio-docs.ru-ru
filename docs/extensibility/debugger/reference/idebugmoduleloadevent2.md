---
title: IDebugModuleLoadEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModuleLoadEvent2
helpviewer_keywords:
- IDebugModuleLoadEvent2 interface
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8fc70ffa1827c69df1567b7f667031b629dcb8bc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918698"
---
# <a name="idebugmoduleloadevent2"></a>IDebugModuleLoadEvent2
Этот интерфейс отправляется ядром отладки (DE) диспетчер отладки сеансов (SDM) при загрузке или выгрузке модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugModuleLoadEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для отчетов, что модуль был загружен или выгружен. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 DE создает и отправляет этот объект события отчета модуль был загружен или выгружен. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны метод `IDebugModuleLoadEvent2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|Возвращает модуль, для которого создается загрузке или выгрузке.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio использует это событие, чтобы сохранить **модули** окно в актуальном состоянии.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)