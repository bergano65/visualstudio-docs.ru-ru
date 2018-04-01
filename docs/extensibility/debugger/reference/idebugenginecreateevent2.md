---
title: IDebugEngineCreateEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5a49af7e9cec830ae3ecfb94ac07dfba68fe8344
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
Модуль отладки (DE) отправляет этот интерфейс диспетчера сеанса отладки (SDM) при создании экземпляра DE.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEngineCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс как часть его нормальной работы. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM `QueryInterface` метод для доступа к `IDebugEvent2` интерфейс).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE создает и отправляет этот объект события, когда был создан экземпляр DE. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEngineCreateEvent2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Извлекает объект, представляющий только что созданный отладчик (DE).|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)