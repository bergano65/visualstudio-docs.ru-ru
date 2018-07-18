---
title: IDebugStackFrame3 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 635b53bf63eb83cc868e4bf9b7d5fbb31fe5aa08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120626"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Этот интерфейс расширяет интерфейс [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) обрабатывать перехваченного исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс на тот же объект, реализующий [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс для поддержки перехваченного исключения.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugStackFrame2` интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Обрабатывает исключение для текущего кадра стека до какой-либо обработки регулярных исключение.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Возвращает контекст кода, в случае очистки стека.|  
  
## <a name="remarks"></a>Примечания  
 Перехваченного исключения означает, что отладчик может обрабатывать исключения перед вызовом любой подпрограммы обработки обычное исключение по времени выполнения. Перехват исключения по существу означает время выполнения представьте, что есть обработчик исключений, даже в том случае, когда не существует.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) вызывается в процессе все события обратного вызова обычное исключение (Единственное исключение — при отладке смешанного кода (управляемого и неуправляемого кода), в этом случае не может быть перехвачено исключение во время вероятность последнего обратного вызова). Если они не реализуют DE `IDebugStackFrame3`, или DE возвращает сообщение об ошибке из IDebugStackFrame3::`InterceptCurrentException` (такие как `E_NOTIMPL`), то отладчик будет обрабатывать исключение, обычно.  
  
 Перехватывая исключение, отладчик можно разрешить пользователю изменять состояние отлаживаемой программы и затем возобновить выполнение в точке, где возникло исключение.  
  
> [!NOTE]
>  Перехваченного исключения разрешены только в управляемом коде, то есть, в программе, которая работает под Common Language Runtime (CLR).  
  
 Модуль отладки означает, что он поддерживает перехват исключения, задав «metricExceptions» в значение 1 во время выполнения с помощью `SetMetric` функции. Дополнительные сведения см. в разделе [SDK вспомогательные методы для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)