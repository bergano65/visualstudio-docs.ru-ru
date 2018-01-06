---
title: "IDebugProcessEx2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2
helpviewer_keywords: IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3d23b1b97145b5e0b24ebfe814aeca5168ef6a06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
|Метод|Описание:|  
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