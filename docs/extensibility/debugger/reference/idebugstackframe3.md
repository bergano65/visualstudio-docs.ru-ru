---
title: "IDebugStackFrame3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3"
helpviewer_keywords: 
  - "Интерфейс IDebugStackFrame3"
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс расширяет [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) обрабатывать перехваченные исключения.  
  
## Синтаксис  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс на одном и том же объекта, реализующего [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс для поддержки перехваченные исключения.  
  
## Замечания для вызывающих объектов  
 Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugStackFrame2` интерфейс для получения этого интерфейса.  
  
## Методы в том порядке Vtable  
 Помимо методов, наследуемых из [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)"  `IDebugStackFrame3` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Обрабатывает исключение для текущего кадра стека перед любым обычным обработкой ошибок.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Возвращает контекст кода очистки было произойти, если стек.|  
  
## Заметки  
 Перехваченное исключение означает, что отладчик может обрабатывать исключение до обычных подпрограмм обработки ошибок вызываются во время выполнения.  Перехватывать исключение по существу означает, что время выполнения, что претендуйте наличии обработчика исключений, даже если их нет.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) вызывается при выполнении всех обычных событий обратного вызова исключений \(единственное исключение из этого при отладке, управляемый код в смешанном режиме \(и неуправляемого кода\), то в этом случае нельзя перехватить исключение во время обратного вызова последнего вероятность\).  Если не реализует DE `IDebugStackFrame3`или DE возвращает ошибку из IDebugStackFrame3::`InterceptCurrentException` \(например,  `E_NOTIMPL`\), затем отладчик будет обрабатывать исключение обычно.  
  
 Можно перехватывать исключение, отладчик может позволить пользователю, чтобы сделать изменения состояния отлаживаемой программы, а затем возобновить выполнение в точке, где было выброшено исключение.  
  
> [!NOTE]
>  Перехваченные исключения могут находиться только в управляемом коде, т е в программе, запущенная под среды CLR.  
  
 Обработчик отладки означает, что он поддерживает перехват исключения путем установки "metricExceptions" со значением 1 во время выполнения с помощью `SetMetric` функция.  Дополнительные сведения см. в разделе [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)