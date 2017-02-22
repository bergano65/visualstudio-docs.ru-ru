---
title: "IDebugStackFrame3::InterceptCurrentException | Microsoft Docs"
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
  - "IDebugStackFrame3::InterceptCurrentException"
helpviewer_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вызывается отладчиком в текущем кадре стека, когда он становится потребоваться перехватывать текущее исключение.  
  
## Синтаксис  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```c#  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### Параметры  
 `dwFlags`  
 \[in\] определяет различные действия.  В настоящее время только [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) Значение  `IEA_INTERCEPT` поддерживается и должен быть задан.  
  
 `pqwCookie`  
 \[out\] уникальное значение, определяющее заданное исключение.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
 Следующие наиболее распространенной ошибка возвращается.  
  
|Ошибка|Описание|  
|------------|--------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Текущее исключение не могут быть перехвачены.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Текущий кадр выполнения не был поиск обработчика.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Этот метод не поддерживается для этого кадра.|  
  
## Заметки  
 Исключение возникает, когда элемент управления увеличений отладчика от времени выполнения на ключевых этапах в процессе обработки исключений.  Во время этих ключевых моментов отладчик может запросить текущий кадр стека, если кадр нужно перехватить исключение.  Таким образом, существенно перехваченное исключение обработчик исключений во время работы для кадра стека, даже если кадр стека, отсутствует обработчик исключения \(например, блок try\/catch в программном коде\).  
  
 Когда отладчик должен знать, если исключение должно перехвачено, он вызывает этот метод на текущем объекте кадра стека.  Этот метод отвечает за обработку все сведения о исключения.  Если [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) не реализован интерфейс или  `InterceptStackException` метод возвращает любую ошибку, то отладчик продолжает обрабатывать исключение обычно.  
  
> [!NOTE]
>  Исключения могут быть перехвачены только в управляемом коде, т е отлаживаемой программы, когда выполняется с временем выполнения .NET.  Конечно, сторонним разработчикам языков могут реализовывать `InterceptStackException` в них обработчиков отладки, чтобы выбрать.  
  
 После завершения отсекаемый отрезок [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) сигнализирует.  
  
## См. также  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)