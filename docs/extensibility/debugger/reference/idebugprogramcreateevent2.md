---
title: IDebugProgramCreateEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1213f37fbf4d7384155a17a5cf42c60b5d544f30
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915037"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Этот интерфейс отправляется ядром отладки (DE) диспетчер отладки сеансов (SDM) при присоединении к программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE или поставщика пользовательского порта реализует этот интерфейс, чтобы сообщить, что программа будет создан, обычно во время исполняемой программы к. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM `QueryInterface` метод для доступа к `IDebugEvent2` интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 DE или поставщика пользовательского порта создает и отправляет этот объект события для создания программы отчетов. DE отправляет данное событие с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, если он присоединен к отлаживаемой программы. Поставщик настраиваемого порта отправляет это событие с помощью [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) интерфейс.  
  
## <a name="remarks"></a>Примечания  
 DE или пользовательский порт поставщик публикует новый [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс путем вызова [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)