---
title: "IDebugBinder | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder"
helpviewer_keywords: 
  - "Интерфейс IDebugBinder"
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugBinder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс привязывает поле символа, обычно возвращаемые поставщиком символов в контексте памяти или объект, содержащий текущее значение символа.  
  
## Синтаксис  
  
```  
IDebugBinder : IUnknown  
```  
  
## Примечания для разработчиков  
 Этот интерфейс поддерживает вычисление выражений и должен быть реализован механизм отладки \(DE\).  
  
## Примечания для вызывающих объектов  
 Этот интерфейс используется в процессе вычисления выражений и обычно используется в реализации [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBinder`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Привязка](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Возвращает контекст памяти или объект, содержащий текущее значение символа.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Определяет тип объекта во время выполнения.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Преобразует адрес памяти или расположение объекта в контексте памяти.|  
|[GetFunctionObject](../Topic/IDebugBinder::GetFunctionObject.md)|Возвращает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) объект, используемый для создания параметров функции.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Возвращает точный тип для переменной.|  
  
## Заметки  
 Этот интерфейс возвращает объекты, используемые средством оценки выражений в синтаксический анализ деревьев. Средство оценки выражений выполняет синтаксический анализ выражения с помощью поставщика символов для преобразования символов в выражении для экземпляров [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), которые описывают каждый символ, с точки зрения его тип и расположение в исходном коде.[Привязка](../../../extensibility/debugger/reference/idebugbinder-bind.md) Метод преобразует `IDebugField` объектов [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) тип объектов, которые подключиться или выполнить привязку символа на фактическое значение в памяти. Эти `IDebugObject` объекты затем сохраняются в дерево синтаксического анализа для дальнейшего определения.  
  
## Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)