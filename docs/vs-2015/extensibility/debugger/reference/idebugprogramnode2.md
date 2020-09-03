---
title: IDebugProgramNode2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1188f18e4a6f604dfd82991433bc0ffe0a07ad47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148563"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет программу, которую можно отладить.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) или поставщик пользовательского порта реализует этот интерфейс для представления программы, которую можно отладить. Этот интерфейс обычно реализуется для того же объекта, который реализует интерфейс [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Этот интерфейс регистрируется с [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] помощью вызова [публишпрограмноде](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [жетпровидерпрограмноде](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) , чтобы вернуть этот интерфейс. Поставщик пользовательского порта получает этот интерфейс через вызов [аддпрограмноде](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Объект DE получает этот интерфейс через вызов для [присоединения](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProgramNode2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Возвращает имя программы.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Возвращает имя процесса, в котором размещена программа.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Возвращает идентификатор системного процесса для процесса, размещающего программу.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Не рекомендуется. НЕ ИСПОЛЬЗУЙТЕ.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Не рекомендуется. НЕ ИСПОЛЬЗУЙТЕ. Альтернативный подход см. в интерфейсе [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) .|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Возвращает имя и идентификатор для отмены выполнения этой программы.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Не рекомендуется. НЕ ИСПОЛЬЗУЙТЕ.|  
  
## <a name="remarks"></a>Remarks  
 Диспетчер отладки сеансов (SDM) обычно вызывает [жетпровидерпрограмноде](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) для получения этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [аддпрограмноде](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [ремовепрограмноде](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Вновь](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [жетпровидерпрограмноде](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
