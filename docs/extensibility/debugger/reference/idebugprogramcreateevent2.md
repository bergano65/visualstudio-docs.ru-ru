---
title: IDebugProgramCreateEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d2bffb1a4a884fe0e6601a6056273e9679a3e6cd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Этот интерфейс отправляется подсистема отладки (DE) диспетчера сеанса отладки (SDM) при присоединении к программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE или пользовательский порт поставщика реализует этот интерфейс для отчетов, что программа будет создана, обычно во время исполняемой программы. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс. Использует SDM `QueryInterface` метод для доступа к `IDebugEvent2` интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE или пользовательский порт поставщика создает и отправляет этот объект события для создания программы. DE отправляет это событие, используя [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы. Поставщик настраиваемого порта отправляет это событие с помощью [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) интерфейса.  
  
## <a name="remarks"></a>Примечания  
 Поставщику другой номер порта или DE публикует новый [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейса путем вызова [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
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