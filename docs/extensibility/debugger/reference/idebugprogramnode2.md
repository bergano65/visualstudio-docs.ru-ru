---
title: IDebugProgramNode2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1fd14fb79d410aa20392af42e43004f46dfec73
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121018"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Этот интерфейс представляет программы, можно отлаживать.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуля отладки (DE) или пользовательский порт поставщик реализует этот интерфейс для представления, можно отлаживать программы. Обычно этот интерфейс реализуется на тот же объект, реализующий [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейса. Этот интерфейс зарегистрирована [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] путем вызова [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) для возврата этого интерфейса. Пользовательский порт поставщика получает этого интерфейса через вызов [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). DE получает этого интерфейса через вызов [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProgramNode2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Возвращает имя программы.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Получает имя процесса размещения программы.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Получает идентификатор процесса системы для размещения программы процесса.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|РЕКОМЕНДУЕТСЯ К ИСПОЛЬЗОВАНИЮ. НЕ СЛЕДУЕТ ИСПОЛЬЗОВАТЬ.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|РЕКОМЕНДУЕТСЯ К ИСПОЛЬЗОВАНИЮ. НЕ СЛЕДУЕТ ИСПОЛЬЗОВАТЬ. В разделе [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейс альтернативный подход.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Возвращает имя и идентификатор DE, выполнение программы.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|РЕКОМЕНДУЕТСЯ К ИСПОЛЬЗОВАНИЮ. НЕ СЛЕДУЕТ ИСПОЛЬЗОВАТЬ.|  
  
## <a name="remarks"></a>Примечания  
 Диспетчер сеансов отладки (SDM) обычно вызывает [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) для получения этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)