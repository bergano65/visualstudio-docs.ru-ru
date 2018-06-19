---
title: IDebugThread2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d93744e55a3e516a131e772fd2df09da5ec23168
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121330"
---
# <a name="idebugthread2"></a>IDebugThread2
Этот интерфейс представляет поток, выполняющийся в приложении.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления с потоком выполнения в одной программе.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) получить этот интерфейс, представляющий текущего активного потока.  
  
 Этот интерфейс также используется при создании запроса точки останова (см. [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).  
  
 Этот интерфейс также возвращается при разрешении привязки или ошибка точки останова (см. [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) и [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugThread2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Извлекает список кадров стека для данного потока.|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Возвращает имя потока.|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Задает имя потока.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Возвращает программу, в котором выполняется поток.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Определяет, можно ли задать следующий оператор к контексту стека данного кадра и код.|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Задает следующий оператор к контексту стека данного кадра и код.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Получает идентификатор потока системы.|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Приостанавливает поток.|  
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Возобновляет работу потока.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Возвращает свойства, описывающие поток.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Возвращает логический поток, связанный с этой физическом потоке.|  
  
## <a name="remarks"></a>Примечания  
 Так как в одном физическом потоке можно использовать несколько программ, более чем на одном `IDebugThread2` из более чем одной программы может представлять том же физическом потоке.  
  
 В случае точки останова или исключения событие передается с помощью [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Один из аргументов в этот метод является `IDebugThread2` интерфейс, представляющий текущий поток. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) используется для получения [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) интерфейса для текущего кадра стека.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)