---
title: "IDebugExceptionEvent2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2
helpviewer_keywords: IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc6dacbac1092e211ba129417bd4e47aea31b733
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Модуль отладки (DE) отправляет этот интерфейс диспетчера сеанса отладки (SDM) при возникновении исключения в программу, выполняемую в данный момент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для отчетов, что исключение произошло в отлаживаемой программы. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE создает и отправляет этот объект события, сообщения об исключении. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugExceptionEvent2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Получает подробные сведения об исключении, запустившем это событие.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Возвращает понятное описание исключение, которое выдается, запустившем это событие.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Определяет, поддерживает ли модуль отладки (DE) передать это исключение для отлаживаемой при возобновлении выполнения программы.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Определяет исключение должны быть переданы отлаживаемой при возобновлении выполнения программы, или если исключения не следует использовать.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Примечания  
 Перед его отправкой, DE проверяется, если это событие исключения назначен первичных или вторичных исключение по предыдущим вызовом [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Если он был определен для исключения первого шанса `IDebugExceptionEvent2` SDM записывается событие. В противном случае DE предоставляет приложению возможность обработки исключения. Если предоставленный обработчик исключения и исключение, обозначенный как второй экземпляр исключения, `IDebugExceptionEvent2` SDM записывается событие. В противном случае DE возобновляет выполнение программы и операционной системы, и среда выполнения обрабатывает исключение.  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)