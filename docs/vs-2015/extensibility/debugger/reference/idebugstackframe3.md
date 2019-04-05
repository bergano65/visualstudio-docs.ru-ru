---
title: IDebugStackFrame3 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 261e71173e98e0ccee5e37f1c37d5825c42f5d93
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990248"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс расширяет [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) обрабатывать перехваченные исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс на тот же объект, реализующий [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс для поддержки перехваченные исключения.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на `IDebugStackFrame2` интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Обрабатывает исключение для текущего кадра стека, прежде чем какой-либо обработки регулярных исключение.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Возвращает контекст кода, в случае очистки стека.|  
  
## <a name="remarks"></a>Примечания  
 Перехваченные исключения означает, что отладчик может обрабатывать исключения, до вызова средой выполнения любой подпрограммы обработки обычное исключение. Перехват исключения по сути означает, что среда выполнения представьте, что имеется обработчик исключений, даже в том случае, когда не.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) вызывается во время все события обратного вызова обычное исключение (Единственное исключение — при отладке смешанного кода (управляемый и неуправляемый код), в этом случае нельзя перехватить исключение во время обратный вызов последней). Если не реализует DE `IDebugStackFrame3`, или DE возвращает сообщение об ошибке из IDebugStackFrame3::`InterceptCurrentException` (такие как `E_NOTIMPL`), то отладчик будет обрабатывать исключение обычно.  
  
 Путем перехвата исключений, отладчик может открыть пользователю внести изменения состояния отлаживаемой программы, а затем возобновить выполнение в точке, где возникло исключение.  
  
> [!NOTE]
>  Перехваченные исключения допускаются только в управляемом коде, то есть в программе, которая работает в группе Common Language Runtime (CLR).  
  
 Модуль отладки указывает, что он поддерживает перехват исключения, задав «metricExceptions» в значение 1 во время выполнения с помощью `SetMetric` функции. Дополнительные сведения см. в разделе [вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
