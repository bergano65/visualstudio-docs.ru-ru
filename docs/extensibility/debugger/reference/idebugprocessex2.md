---
title: IDebugProcessEx2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 479206b75325c1b7e6bba0e4cc4e9b53944d73d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Этот интерфейс позволяет сеанса, диспетчер отладочной (SDM) уведомления процесса, присоединение или отсоединение от процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик пользовательский порт реализует этот интерфейс на один и тот же объект как [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс для:  
  
-   Поддержка отслеживания сеансы, подключенные к процессу  
  
-   Поддержка автоматического присоединения через несколько обработчиков отладки  
  
 Пользовательский порт поставщика можно реализовать этот интерфейс, если он выбирает.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
  
-   Вызовы SDM [QueryInterface](/cpp/atl/queryinterface) на `IDebugProcess2` интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProcessEx2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Сообщает процесс, что сеанс теперь отлаживаемого процесса.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Сообщает процесс, что сеанс больше не является отладка процесса.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Добавляет узлы программы список отладчики.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс является частным между SDM и процесса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)