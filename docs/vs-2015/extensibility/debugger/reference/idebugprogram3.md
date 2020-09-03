---
title: IDebugProgram3 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6de25108cf93314db17a2ac8de9ce8b1dcaed2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148607"
---
# <a name="idebugprogram3"></a>IDebugProgram3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет программу, выполняемую в процессе, и расширяет [EXECUTE](../../../extensibility/debugger/reference/idebugprogram2-execute.md) , предоставляя сведения о потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) и поставщик пользовательского порта реализуют этот интерфейс для представления программы в процессе. Диспетчер отладки сеансов (SDM) также реализует этот интерфейс для предоставления сведений для [присоединения](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Событие [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) возвращает этот интерфейс для новой программы. Этот интерфейс также используется в качестве параметра для многих методов в нескольких интерфейсах.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProgram3` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Выполняет программу. Поток возвращается, чтобы предоставить сведения отладчика о том, какой поток пользователь просматривает при выполнении.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Remarks  
 Программа — это контейнер потоков, выполняющийся в определенной архитектуре среды выполнения, в то время как процесс состоит из одной или нескольких программ.  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Программа](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Очеред](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Журнале](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Вновь](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [дестройпрограм](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Журнале](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
